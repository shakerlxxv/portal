# Portal - An Elixir Inroduction

See https://howistart.org/posts/elixir/1

## Usage

```
  # Start the interactive shell from the project's root directory
  $ iex --sname room1 --cookie secret -S mix

  # Initialize the Door processes you are going to use
  iex(room1@laptop)> Portal.shoot(:green)
  {:ok, #PID<0.95.0>}
  iex(room1@laptop)> Portal.shoot(:red)
  {:ok, #PID<0.97.0>}

  # Start the Portal transfer with configuration
  iex(room1@laptop)3> green = {:green, :"room1@laptop"}
  {:green, :room1@laptop}
  iex(room1@laptop)4> red = {:red, :"room1@laptop"}
  {:red, :room1@laptop}
  iex(room1@laptop)5> p = Portal.transfer(green, red, ['h','e','l','l','o'])
  #Portal<
    {:green, :room1@laptop} <=> {:red, :room1@laptop}
    ['h', 'e', 'l', 'l', 'o'] <=> []
  >

  # Run the transfers between doors
  iex(room1@laptop)6> Portal.push_right(p)
  #Portal<
    {:green, :room1@laptop} <=> {:red, :room1@laptop}
         ['h', 'e', 'l', 'l'] <=> ['o']
  >

  iex(room1@laptop)7> Portal.push_right(p)
  #Portal<
    {:green, :room1@laptop} <=> {:red, :room1@laptop}
         ['h', 'e', 'l'] <=> ['l', 'o']

```

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add portal to your list of dependencies in `mix.exs`:

        def deps do
          [{:portal, "~> 0.0.1"}]
        end

  2. Ensure portal is started before your application:

        def application do
          [applications: [:portal]]
        end
