# Prompts compartilhados do Codex

Use estes prompts a partir da raiz do workspace `softwares`. Informe `project_ids=[...]` usando os IDs exatos de `workspace.yaml`; em uma tarefa direcionada a um projeto, informe também `target_project_id`. Não infira o projeto pelo diretório atual ou pelo tipo do projeto. As skills compartilhadas ficam em `plugins/codex-software-skills/skills/`. Resolva o caminho de cada projeto pelo manifesto, leia o `AGENTS.md` mais próximo e consulte os `workflow_files` daquele projeto. Estes prompts complementam as instruções do workspace e dos projetos; não as substituem.

## 1. Entender um repositório

> Leia primeiro `plugins/codex-software-skills/skills/references/project-scope.md` e valide `project_ids` em `workspace.yaml`. Para cada projeto selecionado, resolva `path` a partir da raiz do workspace e leia o `AGENTS.md` mais próximo e os `workflow_files` aplicáveis. Leia os documentos de objetivos, planejamento e harness que existirem naquele projeto, além do código-fonte e dos testes relevantes. Informe os fatos observados sobre cada repositório, branch e worktree, os comandos de validação confirmados e os requisitos ainda não resolvidos. Mantenha esta etapa somente para leitura. Não deduza requisitos de produto a partir de detalhes da implementação.

## 2. Preparar ou revisar uma fase

> Leia `plugins/codex-software-skills/skills/references/project-scope.md`, valide `project_ids` em `workspace.yaml` e, para cada projeto selecionado, consulte o `AGENTS.md`, os `workflow_files`, os objetivos e os documentos de planejamento aplicáveis. Faça uma análise inicial somente para leitura. Proponha uma fase delimitada, vinculada a um objetivo aprovado, com escopo, itens fora do escopo, dependências, arquivos afetados, decisões humanas, critérios de aceitação, etapas de TDD e verificação, riscos, evidências e uma condição de parada. Se faltarem requisitos ou prioridades, identifique a decisão necessária sem inventar um roadmap. Antes de alterar arquivos de planejamento, resuma os arquivos e as mudanças exatos e aguarde aprovação.

## 3. Executar uma fase aprovada

> Valide `project_ids` em `workspace.yaml` e leia `plugins/codex-software-skills/skills/run-harness/SKILL.md`. Para uma Issue, siga também `plugins/codex-software-skills/skills/implement-issue/SKILL.md` e consulte os `workflow_files` do projeto-alvo. Passe a lista original completa de `project_ids` e o `target_project_id` exato em cada handoff. Se uma skill, procedimento ou comando exigido não estiver disponível no manifesto ou nas instruções do projeto, pare e peça a informação necessária.
> Primeiro, inspecione a árvore de trabalho, a branch, o código afetado e os testes sem editar arquivos. Resuma o escopo autorizado, os arquivos exatos e o plano de verificação. Implemente somente essa fase. Para mudanças de comportamento, escreva um teste focado que falhe, confirme a falha, implemente a menor alteração que o faça passar e depois refatore enquanto as verificações continuarem aprovadas. Execute somente os comandos de validação confirmados para o projeto-alvo. Não execute migrações em bancos reais. Registre apenas evidências observadas e pare no ponto de handoff definido pela skill aplicável.

## 4. Verificar e reunir evidências

> Leia os critérios de aceitação da fase, o `AGENTS.md` do projeto-alvo, o diff relevante, os testes e os comandos de validação confirmados em `workspace.yaml`. Para QA de uma Issue, siga `plugins/codex-software-skills/skills/qa-issue/SKILL.md` e examine o commit exato indicado pelo workflow. Inspecione as alterações e execute as verificações pertinentes mais específicas. Informe os comandos exatos e os resultados observados, as verificações ignoradas ou indisponíveis e os respectivos motivos, regressões e limitações restantes. Não edite arquivos nem afirme que verificações passaram sem observar a saída.

## 5. Revisar ou corrigir

> Revise o diff em relação à fase aprovada, aos critérios de aceitação, ao `AGENTS.md` do projeto-alvo e aos `workflow_files` aplicáveis. Apresente problemas acionáveis por gravidade, com referências aos arquivos e evidências. Para corrigir, informe primeiro o escopo proposto, os arquivos e as verificações; aguarde autorização, a menos que o usuário já tenha autorizado essa correção. Preserve a lista original de `project_ids` e não avance para outra fase.

## 6. Encerrar uma fase e transferir o trabalho

> Leia o arquivo da fase e o contexto do projeto-alvo, se existirem, além do diff atual, dos resultados de verificação e dos apontamentos de revisão. Atualize os registros de fase do próprio projeto somente quando fizerem parte do escopo autorizado. Para tarefas multiprojeto, mantenha o registro de subtarefas exigido por `plugins/codex-software-skills/skills/run-harness/SKILL.md`. Marque uma fase como concluída somente quando houver evidências dos critérios de aceitação, das verificações exigidas e das condições de revisão; mantenha lacunas visíveis. Resuma os arquivos alterados, a validação, as limitações e a próxima ação sem iniciá-la. Siga o handoff definido pelas skills compartilhadas e não execute operações Git sem a autorização correspondente.
