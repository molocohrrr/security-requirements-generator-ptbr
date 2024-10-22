# Sobre
Gerador de requisitos de segurança de aplicativos, baseado em ASVS, guia de testes OWASP e alguma experiência :-)

## O que fizemos
- Dividimos os requisitos do ASVS por funcionalidade
- Adicionamos uma função para marcar alguns requisitos como importantes (para que seus desenvolvedores possam começar a partir deles, por exemplo)
- Mapeamos os requisitos para os testes
- Compartilhamos para você neste repositório e [em nosso subdomínio](https://requirements.whitespots.io/en)

# Clone
```bash
git clone https://github.com/molocohrrr/security-requirements-generator-ptbr.git srg && \
cd srg
```

# Deploy
## Server
```bash
export BASE_URL=http://hostname.com
docker-compose up -d --build
docker-compose run back migrate
docker-compose run back loaddata
docker-compose run back collectstatic
docker-compose exec back ./manage.py create_super_user --username admin --password PASSWORD # atenção à mudança destas senhas em produção
open https://hostname.com/admin/  # no navegador
```

# FAQ
### Como adicionar minhas próprias categorias (funções de aplicativo), requisitos e testes?
1. Basta visitar <your_host>/admin e fazer login no administrador do Django
2. Vá para categories/requirements/tests (depende do que você deseja adicionar/editar)
3. Depois disso, execute `docker-compose run back dumpdata`
Ele fará um dump de todas as suas categorias, requisitos e configurações de testes atuais

### Como contribuir com categorias, requisitos, testes?
Isso não cobrirá TODOS os requisitos possíveis, descritos no OWASP ASVS completo.
Em vez disso, esta ferramenta foi projetada para ajudar pequenas equipes a seguir as coisas mais importantes e relevantes.

1. Antes de adicionar algo novo, tente encontrar o mesmo requisito/teste/categoria em dados existentes
2. Sinta-se à vontade para descrever melhor os testes/requisitos existentes
3. Descreva suas alterações na solicitação de mesclagem
- Coloque suas alterações em um título: Nova categoria/Novos requisitos/Novos testes
- Descreva no texto quais problemas foram resolvidos e quais não foram