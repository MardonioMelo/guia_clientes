# Guia de Clientes

Projeto criado no curso de VueJS seguindo a [playlist das aulas ](https://youtube.com/playlist?list=PLJ_KhUnlXUPteacVhunyK5M8SKIadeED0) no YouTube.

## Video #3 - Ambiente de desenvolvimento
- Instalar node.js e NPM ou Yarn
- Instalar VsCode
- Instalar o Vue CLI 

```
$ npm install -g @vue/cli
```
ou
```
$ yarn global add @vue/cli
```
## Video #4 - Como criar um projeto

Entre no local onde deseja criar o projeto e execute o comando
```
$ vue create nome_do_projeto
```
Para subir o projeto para o gitHub, crie um novo repositório no gitHub com o o mesmo nome que você criou o projeto local com o Vue-CLI. Após criar o repositório no GitHub e o projeto localmente com o mesmo nome, execute o comando para configurar a origem do repositório:
```
$ git remote add origin <repo-url>
$ git push origin master
```
Depois escolha o gerenciador de pacotes/ projeto NPM ou Yarn. 
Após o projeto criado, entre na pasta do projeto e execute o comando para rodar o projeto em um servidor local na porta 8080. Se você escolheu o gerenciado de pacotes NPM execute
```
$ npm run serve
```
ou se escolheu o Yarn
```
$ yarn serve
```
>Eu escolhi o Yarn por ser mais rápido

### Configuração do projeto
```
yarn install
```

### Compila e hot-reloads para desenvolvimento
```
yarn serve
```

### Compila e minimiza para produção
```
yarn build
```

### Lista e conserta arquivos
```
yarn lint
```

### Personalize a configuração
Veja [Configuration Reference](https://cli.vuejs.org/config/).
