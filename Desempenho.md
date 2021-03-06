# Desempenho do Servidor

Gostaria da opinião de colegas que têm experiências parecidas.

Até hoje tenho usado sites em hospedagem compartilhada ou em VPS usando Ubuntu e Apache.

Agora estou testando VPS na DigitalOcean e me parece que 1GB da RAM oferecido agora não dá o desempenho de 512 há algum tempo.

Então comecei a repensar minhas escolhas. Primeiro mudei para Debian. Não tive a facilidade de usar o ufw na versão 9.3 do Debian e desisti. Depois fui testar o nginx, que dizem ter melhor desempenho que o Apache. Também tive dificuldades em configurar com php e desisti.

Acontece que estou gostando do DO e como está com Ubuntu e Apache não tá dando para usar o plano menor.

Então decidi usar o Debian 9.3 com iptables e pesquisar bem o uso do nginx. Desta vez, com mais interesse, deu certo. Fui tendo um problema e fui resolvendo. Esta sensação de poder/controle me agrada.

Logo percebi as leves diferenças de desempenho. Agora com Debian 9.3, nginx e iptables me parece que o site fica melhor.

Então usar a ferramenta online:
https://tools.pingdom.com/ (Website speed teste). Ela me fala várias coisas, entre elas que meu novo site, com Debian e cia tem um Load time de 1.11 segundos enquanto a outra com Debian fica com 3.70 segundos. O antigo era melhor que os 43% de sites testados enquanto que usando Debian e cia é melhor que 87% dos testados.

Gostaria de "ouvir" o que tem a dizer outros colegas que passaram por algo assim.

O servidor com Ubuntu já está usando swap, enquanto quue o com Debian não está.

Edson Correia  no Joomla Brasil - Ribamar FS é praticamente impossível listar todos os fatores que podem deixar um servidor mais rápido ou mais lento. É uma mistura de hardware com software, configurações finas, largura de banda, quantidade de acessos, localização do servidor, etc. Se formos analisar os aspectos isolados, sim: Nginx é extremamente mais rápido que o Apache, pelo fato de não ter diversas funcionalidades extras que o Apache tem, mas que não fazem falta para a grande maioria dos sites. Outra coisa que faz o site acelerar bastante, principalmente o nosso amado Joomla, é o PHP 7. Há um ganho de velocidade perceptível entre o 7 e o 5.6. Eu também uso Digital Ocean e vi que eles atualizaram os planos, mas não sei quanto ao desempenho como mencionou... Não duvido que tenham piorado em certa medida, pois não existe almoço grátis... Mas, pode ser também que você esteja experimentando performances diferentes diante das diversas opções de sistema operacional / servidor web que tem testado. Eu sigo os tutoriais do site Fator Binário que são muito bons e ensinam como montar um Debian com ISPConfig que usa Nginx e fica bastante rápido. Depois dá uma olhada lá.

Rafael Oliveira de Santana  no Joomla Brasil
Edson já respondeu tudo. Só adicionando uma informação.... Digital Ocean, Vultr e Linode são as melhores opções custo benefício em Vps. Escolha uma opção que tenha uma latência baixa. As do Sul do EUA por exemplo. Na Vultr tem a opção de Miami... Média de 400 ms. Em termo de hardware, latência eu acho melhor, bem acompanhado da Linode e depois a Digital Ocean. No fator binário o foco é utilizar o ispconfig, um painel free e ótima alternativa ao pago Cpanel. Utilizando nginx no debandada. Assim, como tutoriais relacionado de segurança, email. Tudo pra vc gerenciar seus sites de forma fácil, sem ser na mão.

https://developers.google.com/speed/pagespeed/insights/

## Sugestões de otimização

Precisa antes saber se o servidor oferece suporte

- Ativar compactação
- Eliminar JavaScript e CSS de bloqueio de renderização no conteúdo acima da borda
- Aproveitar cache do navegador
- Otimizações já implementadas
- Compactar CSS 
- Sua CSS está reduzida. Saiba mais sobre como reduzir a CSS.
- Compactar HTML
- Seu HTML está reduzido. Saiba mais sobre como reduzir o HTMLl.
- Compactar JavaScript
- Seu conteúdo JavaScript está reduzido. Saiba mais sobre como reduzir o JavaScript.
- Evitar redirecionamentos da página de destino
- Sua página não tem redirecionamentos. Saiba mais sobre como evitar os redirecionamentos da página de destino.
- Otimizar imagens
- Suas imagens estão otimizadas. Saiba mais sobre como otimizar as imagens.
- Priorizar o conteúdo visível
- Você tem conteúdo acima da dobra com a prioridade correta. Saiba mais sobre como priorizar o conteúdo visível.
- Reduzir o tempo de resposta do servidor
- Seu servidor respondeu rapidamente. Saiba mais sobre a otimização do tempo de resposta do servidor.

## Outras ferramentas

- https://www.webpagetest.org/
- https://gtmetrix.com/analyze.html
- https://developers.google.com/speed/pagespeed/insights/
- https://tools.pingdom.com/

Edson Correia no Joomla Brasil Essas compactações automáticas raramente funcionam a contento. Todas as vezes que eu ativei tais otimizações o site quebrou todo. E do que funcionava não ficava tão rápido a ponto de ser perceptível. Então pela minha experiência o que posso dizer é que não esquente tanto com essas pseudo otimizações. É mais efetivo usar um servidor não compartilhado como um vps e usar os métodos nativos do joomla como cache e compressão gzip. Se o servidor tiver caches como APC ou Memcache são melhores que o cache nativo do Joomla. E se puder usar uma CDN como a cloudflare isso também ajuda muito.

