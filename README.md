# Petstore Go Client

This is an API client for Petstore.

## Installation

Installation can be done with a normal `go get`:

```bash
go get -u github.com/TyunTech/go-petstore
```

## Usage

```go
import sdk "github.com/TyunTech/go-petstore"
```

Construct a new Petstore client, then use the various endpoints on the client to
access different parts of the Petstore API. For example, to list
all pets:

```go
config := &sdk.Config{
	Address: "insert-your-petstore-address-here",
}

client, err := sdk.NewClient(config)
if err != nil {
	log.Fatal(err)
}

orgs, err := client.Pets.List(PetListOptions{})
if err != nil {
	log.Fatal(err)
}
```

## Examples

The [examples](https://github.com/scottwinkler/go-petstore/tree/master/examples) directory
contains a couple of examples. One of which is listed here as well:

```go
package main

import (
	"log"

	sdk "github.com/TyunTech/go-petstore"
)

func main() {
	config := &sdk.Config{
		Address: "insert-your-petstore-address-here",
	}

	client, err := sdk.NewClient(config)
	if err != nil {
		log.Fatal(err)
	}

	// Create a new pet
	options := sdk.PetCreateOptions{
        Name:  "mittens",
        Species: "cat",
        Age: 2,
	}

	pet, err := client.Pets.Create(options)
	if err != nil {
		log.Fatal(err)
	}

	// Delete a pet
	err = client.Pets.Delete(pet.ID)
	if err != nil {
		log.Fatal(err)
	}
}
```
