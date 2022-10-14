# AULA 02

**INSTALANDO FRAMEWORKS**
-> npm install -D tailwindcss postcss autoprefixer
    - Post css: bundler que transforma o código tailwind em CSS
-> npx tailwindcss init -p 
    - Criar arquivos de configuração do tailwind e do postcss

**STORYBOOK**
-> É uma ferramenta que permite a visualização dos componentes de forma isolada. Funciona como se fosse uma central
para a documentação dos componentes
-> npx sb init --builder @storybook/builder-vite --use-npm
    - Quando instalamos o storybook ele vem configurado como WebPack, e como o Vite é mais rápido que ele, pois usa o sbuild que é um compilador de código bem mais rápido, por isso passamos o "builder-vite"
-> npm run storybook

**IMPORTAR TOKENS DO FIGMA**
-> Cores para o tailwind.config.cjs
    - Vamos substituir as cores padrão do tailwind pelas nossas do Design System
-> Criar componentes 
    - Text
        - Usar clsx para criar classes de maneira condicional 
          - $ npm install --save clsx
        - npm install @radix-ui/react-slot
    - Heading
    - Button
    - TextInput
      - Conceito de composição
      - Phosphor icons [npm i phosphor-react]
    - Checkbox
      - npm install @radix-ui/react-checkbox
**DECORATORS NO STORYBOOK**
-> São formas de adicionar elementos a mais além do principal que estamos mostrando em tela

# AULA 03

-> Deploy da projeto com a documentação do Storybook través do GitPages
  - Instalar ```npm i @storybook/storybook-deployer --save-dev```
  - Para fazer o deploy vamos precisar que o repositório seja um repo git
    - git init
    - "deploy-storybook": "storybook-to-ghpages" dentro de package.json
    - Agora temos o build-storybook e o deploy-storybook
***Executando arquvisos do package.json***
    - npm run build-storybook
      - Vai criar uma pasta chamada 'storybook-static' que possui todo o conteúdo da nossa documentação do storybook
        em arquivos estáticos (html, css, bundle), para poder ser hospedado em um local
    - Agora vamos adicionar a pasta criada no Gitignore, após isso a página não sera enviada para o github

***Comandos do github***
    - Criar o repositório no github
      - Vamos utilizar a CLI do GIthub, que permite a gente mexer no github através do terminal
      - ```gh auth login```
      - ```gh repo create```
      - ```git add .```
      - ```git commit -m "Initial commit"```
      - ```git remote add origin https://github.com/Henrriky/ignite-lab-design-system.git```
      - ```  git branch -M main```
      - ``` git push -u origin main```
    - Queremos que toda vez que eu envie uma nova versão do código no Github, ele publique o meu storybook dentro do GitPages
      - Para isso, vamos instalar um serviço de integração contínua (nada mais são do que uma forma da gente conseguir disparar ações a cada vez que a gente tem uma nova mudança no nosso código)
        - Além disso, vamos fazer a entrega contínua que é fazer o deploy(colocar no ar) a nossa aplicação (documentação) quando fizermos um código novo
***Instalando o serviço de integração contínua***
    - Vamos criar uma pasta com a seguinte estrutura .github/workflows/deploy-docs.yml
      - Dentro desse arquivo vamos utilizar a sintaxe do próprio github actions
    - Teste:
      - ```git status```
      - ```git add .```
      - ```git commit -m "ci: Add publish storybook workflow"```
      - ```git push origin main```