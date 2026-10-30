# lab-knowledge

What agents (and people) need to know about this environment: network and proxy
gotchas, certificate handling, build containers, bench procedures and safety rules, plus
the lab inventory and the catalog of every agent skill in the GitLab group.

Agents read this through the knowledge MCP server in `agent-platform`
(`search_docs`, `get_doc`, `get_device`, `find_skill`). They never write to it directly.
New knowledge arrives as an MR with `status: draft`, and a human marks it `verified`.

- `docs/`: one Markdown file per fact or procedure, with YAML frontmatter.
- `inventory/`: instruments, boards and benches. These are the only addresses agents
  may use.
- `models/registry.yaml`: which models each model server offers and what each is good
  for. Agents ask `recommend_model("review a diff")`.
- `catalog/`: generated skills index. Don't edit it by hand.
- `BLUEPRINT.md`: schemas and rules. `AGENTS.md`: rules for agents editing this repo.

## Adding a doc

1. Copy `docs/_template.md` to `docs/<area>/<slug>.md`.
2. Fill in the frontmatter. Use `status: draft` until someone has confirmed it on the
   real system.
3. Validate:
   ```
   python3 ~/.local/share/agent-platform/mcp/knowledge/knowledge_core.py validate . --profiles-from ~/.local/share/agent-platform/profiles
   ```
4. Open an MR.

## Search it yourself

```
python3 ~/.local/share/agent-platform/mcp/knowledge/knowledge_core.py search . "proxy llm server"
python3 ~/.local/share/agent-platform/mcp/knowledge/knowledge_core.py skills . "flash board"
python3 ~/.local/share/agent-platform/tools/models.py --knowledge . recommend "read a scope screenshot"
python3 ~/.local/share/agent-platform/tools/models.py --knowledge . list --location corp-llm
```
