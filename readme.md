ansible -i - indicar o arquivo de inventário
-m selecionar o modulo
-a colocar argumento necessário do módulo

ssh-keygen para criar um par de chaves
ssh-copy-id login@server para copiar a chave publica para o servidor de destino

 export ANSIBLE_CONFIG="./ansible.cfg" - configurar para o Ansible usar o arquivo .cfg criado

 módulo apt para instalação de pacote ad hoc
 apt -a "name=pacote state=present" --become (state para instalar)
  state=latest (Instalar o pacote)
 state=absent (Remover o pacote)

 --become para escalar privilégio (usar sudo)

[docs.ansible.com](https://docs.ansible.com/projects/ansible/latest/collections/index_module.html) - Documentação Ansible

setup - coletar informações dos hosts
"filter=filtro" - argumento de filtragem do setup

Playbook - sempre começa com ---
tasks = criar tarefa

ansible-playbook arquivo para executar ansible com playbook

when: (ansible_facts['distribution']=="Rocky Linux") = usar condicional com algum atributo do facts(dados dos hosta do módulo setup)

variáveis podem ser criadas no arquivo inventory ou no playbook
as variaveis podem ser usadas usando "{{ variavel }}" 

Módulo hostname para alterar o nome dos hosts

módulo file para criação de arquivo e diretírio
state pode ser directory para pasta e touch para arquivos

Os atributos abaixo não atualiza os atributos do arquivo
modification_time: preserve
      access_time: preservev

      owner e group servem para definirr o proprietario e o grupo do arquivo

with_items para criar uma lista
variavel item pode ser usado para referenciar essa lista de itens

debug para exibir alguma mensagem na tela durante execução de playbook
módulo msg para exibir mensagem na tela

é possível criar uma lista de variaveis.
var: {
      variavel1,
      variavel2,
      variavel4
}

e na hora de chamar usar var.variavel1

register para capturar a saída de execução de uma tarefa e armazena-la em uma variável

Roles permite o compartilhamento e reutilização de tarefas Ansible

ansible-galaxy init nome da role para criar uma role com sua estrutura

notify faz uma chamada ao arquivo da pasta handlers

lineinflile - escreve em um arquivo - adiciona uma linha em um arquivo
handlers são tarefas que só são executadas quando notificadas.

 include: arquivo para incluir outro arquivo yml em tasks

 incluir tag embaixo do nome da task pode fazer com que ela seja excutada individualmente usando o argumento --tag "nome da tag"