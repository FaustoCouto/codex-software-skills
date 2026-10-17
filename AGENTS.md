# Open Delivery — workspace de software

Esta pasta é o workspace e o repositório de configuração `codex-software-skills`.
Mantenha aqui somente instruções compartilhadas do Codex, skills, manifesto dos
projetos e arquivos auxiliares dessas configurações.

## Projetos e escopo

- Use `workspace.yaml` como fonte de verdade para IDs, nomes, caminhos, remotos,
  rastreadores, comandos de validação e referências de workflow dos projetos.
- Toda skill deste workspace exige `project_ids=[...]` com IDs exatos de
  `workspace.yaml`. Se a lista estiver ausente, inválida, repetida ou ambígua,
  pergunte quais projetos incluir. Nunca infira o escopo pelo diretório atual,
  pelo tipo do projeto ou por suposições.
- Preserve a lista original de `project_ids` em cada handoff. Ao limitar uma
  subtarefa a um projeto, passe também `target_project_id` e confirme que ele
  pertence à lista original; não substitua nem amplie o escopo.
- Resolva cada `path` a partir desta pasta e leia o `AGENTS.md` mais próximo e
  os arquivos de workflow indicados no manifesto antes de trabalhar naquele
  projeto. Execute comandos Git e de validação no repositório filho correto.
  Valores nulos ou ausentes não confirmam remoto, tracker, repositório ou
  comando.
- `open-delivery-api/` e `open-delivery-front/` são pastas de projetos, não
  conteúdo deste repositório de configuração. O `.gitignore` da raiz impede que
  seus arquivos entrem neste repositório; isso não impede a leitura dos arquivos
  quando o escopo solicitado os inclui.
- Não inclua projetos de arte 3D neste workspace.

## Formato do manifesto

Mantenha `schema_version` e `projects`. Cada projeto tem `project_id`,
`display_name`, `path` relativo a esta raiz e `kind`. Use IDs estáveis e
específicos derivados do remoto ou do nome estabelecido do projeto; não use
categorias genéricas como `api` ou `app`. `git_remote`, `issue_tracker`,
`validation_commands`, `workflow_files` e `status` são campos opcionais e só
devem registrar dados confirmados. Use `status: directory-only` quando houver
somente uma pasta, sem repositório Git próprio. Para adicionar um projeto,
  acrescente uma entrada em `projects` com os mesmos campos e tipos, caminho
  existente e comandos e referências encontrados nas instruções do próprio
  projeto. Acrescente referências específicas somente dentro de
  `workflow_files`; não crie um segundo manifesto nem altere o formato dos campos
  comuns para acomodar um projeto novo.

## Regras comuns de trabalho

- Mantenha cada mudança de código dentro do projeto solicitado. Não misture
  código, dependências, configurações, comandos ou artefatos entre projetos.
- Para cada projeto, use seu próprio repositório Git, branch, worktree e PR.
  Execute comandos Git de código a partir do repositório filho correto; nunca
  use o repositório `softwares` como repositório de código.
- Em uma tarefa multiprojeto, preserve a lista original de `project_ids` em
  todos os handoffs. Ao delegar uma subtarefa de um projeto, inclua também
  `target_project_id`, que deve pertencer a essa lista. Registre cada subtarefa
  e seu projeto-alvo. Só conclua a tarefa quando todos os comandos de validação
  confirmados para cada projeto e a validação de integração combinada passarem.
  Se um workflow ou comando necessário não estiver documentado, peça essa
  informação em vez de inventá-la.
- Siga as convenções do `AGENTS.md` mais próximo. Como regra comum, não use
  strings ou números mágicos para comportamento em código de produção; use o
  arquivo de constantes apropriado ao projeto, incluindo chaves de propriedades
  usadas em runtime. Para projetos que executam SQL, mantenha a query visível na
  função ou método que a executa.
- Use somente comandos de validação registrados no manifesto ou confirmados nas
  instruções do projeto. Execute-os no diretório do projeto correspondente.
- Preserve alterações existentes. Não crie commits, faça push, merge ou PR sem
  autorização explícita do usuário. Apresente as alterações para revisão.
