This is a basic tutorial showing how to work with Erlang and Elixir in the workspace.

## Erlang 

### Shell 

The Erlang shell is used for testing of expressions. Start the Erlang shell from a command prompt with the command `erl`   

having started shell, evaluate the following expressions 

```
2 + 5.
(42 + 77) * 66 / 3.

Str = "abcd".
L = length(Str).
```

### Hello world

Go to the Quickstart page, open VS-Code and create file `hello.erl` with the following code 

```
-module(hello).
-export([hello_world/0]).

hello_world() ->
  io:format("Hello, World!~n", []).
```

Now open Terminal, start Erlang shell with `erl` and execute 

```
c(hello).
```

## Elixir

### Shell 

`iex` is a command which stands for Interactive Elixir. 

Openn terminal, start interactive Elixir shell with `iex` and evaluate

```
40 + 8
"hello" <> " world"
```

### Scripts 

Open IDE and create file `hello.exs` with the following code 

```
IO.puts("Hello world from Elixir")
```

In terminal execute 

```
elixir hello.exs
```

### Manage Elixir versions with Kiex

[Kiex](https://github.com/taylor/kiex) allows you to easily build and switch between different Elixir versions.   

List installed versions

```
kiex list
```

List known releases

```
kiex list releases
```

Install a known release

```
kiex install 1.13.0
```

Use specific elixir version

```
kiex use 1.13.0
```

