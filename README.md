# Pizza
The goal of this program is to simulate a content delivery network for an online pizza shop application. Since I don't have access to a whole bunch of edge computers, I am going to simulate the flow and design of a content delivery network locally.

The simulated problem will be simple. We will be mocking a pizza shop. Users will be able to customize the toppings and size of their pizza, and also select from some pre-created specialty pizzas on the menu.

This gives us the ability to play with caching strategies, as some content is dynamic and some is static (i.e. custom pizza vs. pre-created pizza).

## Requirements

### Usage
The user can build or select a pizza, which is composed of the following fields:
- size
- crust type
- sauce type
- cheese type
- toppings

### Origin Server
The origin server will be the source of truth for the pizza ingredients available,
and also the pre-made pizza recipes users can order. The catch: the pizza shop rotates ingredients to keep things interesting, and with that, they also rotate their pre-made selection.

### Edge Server
To help support our simulated globally distributed user-base, we will create `n` edge servers, which are fully specified by their spatial location and URL. Since the origin server rotates ingredients and pre-made pizzas, we get to play around with some caching concepts on the edge servers.

#### DNS
We will mock DNS lookup via a simple routing function that will take requests from users and compute the most optimal server to hit for the request.

### CLI
For the user to actually interact with our pizza shop, we need some way for them to select the ingredients and customize their pizza. To do this, we must create a CLI for them to use.

#### Flow
First, a welcome message will pop up. Then, the user will be prompted to select from one of the specials (the pre-made pizzas), or to create their own. Once the user has selected an option, the CLI will have to query one of the servers to grab the information required for the user to select from. Finally, the user will enter the pizza/ingredients they want, and the CLI will place the order for them.

> [!NOTE]
> Since everything will be running on localhost, we will need to randomly generate a location for the user to exist in so we can properly simulate DNS routing.
