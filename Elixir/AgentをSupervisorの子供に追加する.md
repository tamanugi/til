# AgentをSupervisorの子供に追加する


lib/slash\_bot\_http\_code/application.ex

```
defmodule SlashBotHttpCode.Application do
  # See https://hexdocs.pm/elixir/Application.html
  # for more information on OTP Applications
  @moduledoc false

  use Application

  def start(_type, _args) do

    children = [
      Plug.Adapters.Cowboy.child_spec(:http, SlashBotHttpCode.Router, [], [port: 4000]),
      {SlashBotHttpCode.TestAgent, []}
    ]

    opts = [strategy: :one_for_one, name: SlashBotHttpCode.Supervisor]
    Supervisor.start_link(children, opts)
  end
end

```

lib/slash\_bot\_http\_code/agent.md

```
defmodule SlashBotHttpCode.TestAgent do
  use Agent
  
  def start_link
    Agent.start_link(fn -> %{} end)
  end
end
```

- Agentの方で `use Agent` を追加する
- `{module, arg}` のタプルで supervisorに追加する
