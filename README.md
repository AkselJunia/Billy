# Retrieve raw events data

Your goal is to create a tool that gathers and parses events and related smart contracts information in
order to make them exploitable by the team.

#### Next : 
- Use case
  - Specifications
- Instructions
  - Programming language
  - Why do the coding exercise
  - Timeline to finish the exercise
- Bonus

## Use case

The data we manipulate in our application come from two different sources :

- a `csv file` completed by the events organizers
  that contains all the events information (for example, the event title, the event date, etc.)
- a `json file` containing the information of the new smart contract we deployed on the blockchain. The smart contract is associated with
  the event (using the event id) and contains the information related to the nft collection (ticket collection)

In order to use these data and share them with our partners we would want them to be formatted in a JSON file like the
example below:

```json
[
  {
    "eventId": 1,
    "title": "Mouse Party",
    "startDatetime": "2022-07-10T18:30:00",
    "endDatetime": "2022-07-11T01:00:00",
    "address": "1 Rue Alexandre Avisse 45000 Orléans",
    "locationName": "L'Astrolabe",
    "totalTicketsCount": 500,
    "assetUrl": "https://photos.com/mouseparty.png",
    "lineUp": [
      "Mehdi Maïzi",
      "Rad Cartier",
      "Squidji"
    ],
    "ticketCollections": [
      {
        "collectionName": "Mouse On",
        "scAddress": "KT1AKqxCJH9EPimNm1wo1BEgG9bFRgptJwkk",
        "collectionAddress": "KT1Apf8CPkYBe3bRuTCET6A4NhnosX2BAnp9",
        "pricePerToken": 4,
        "maxMintPerUser": 5,
        "saleSize": 500
      }
    ]
  }
]
```

### Specifications

- The fields name should be in camelCase not in snake_case.
- `lineUp` and `locationName` fields are optional. When the value doesn't exist, the field should be null. 
- `lineUp` field is a list. In the csv file the different names will be separated with "-", they should be separated and put into a list.
- The format of the the asset contained in the `assetUrl` field should be mp4 or png or jpeg. If it's not the case, the field should be null.
- The `scAddress` field corresponds to the "crowdsale" field in the input file `smart-contracts-data.json`. 
The `collectionName` field corresponds to the "collection" field in the input file.

## Instructions

We want a script that takes the two files contained in this repository (`organizers-data.csv` and `smart-contracts-data.json`)
as input and that outputs a `.json` file containing all the formatted events' info as displayed in the previous example.

We expect you to create and share with us a git repository with the code you produced.

### Programming Language

You can use any language (or framework/library) that you feel comfortable with to solve the problem.

### Why do the coding exercise?

We are a technology driven company and we have a passion for clean code.
Coding is a part of our day to day job and the role we offer is very hands-on.
We would like to make sure that anyone who joins us shares these values as well. So show us your passion for coding through this exercise!

### Timeline to finish the exercise

We appreciate you taking the time to do this exercise and as such there is no hard deadline for finishing it. 
Also, we don't want you to spend too much time in solving this exercise by creating very complex solution. 

## Bonus !

If you want to challenge yourself a bit more, you can create a Rest api (that we will launch locally) with any 
framework you want where we will be able to request those same events information (no need to create a database for this part,
you can just use the data you generated locally):

```
GET /events

response : 
[
  {
    "eventId": 1,
    "title": "Mouse Party",
    "startDatetime": "2022-07-10T18:30:00",
    "endDatetime": "2022-07-11T01:00:00",
    "address": "1 Rue Alexandre Avisse 45000 Orléans",
    "locationName": "L'Astrolabe",
    "totalTicketsCount": 500,
    "assetUrl": "https://photos.com/mouseparty.png",
    "lineUp": [
      "Mehdi Maïzi",
      "Rad Cartier",
      "Squidji"
    ],
    "ticketCollections": [
      {
        "collectionName": "Mouse On",
        "scAddress": "KT1AKqxCJH9EPimNm1wo1BEgG9bFRgptJwkk",
        "collectionAddress": "KT1Apf8CPkYBe3bRuTCET6A4NhnosX2BAnp9",
        "pricePerToken": 4,
        "maxMintPerUser": 5,
        "saleSize": 500
      }
    ]
  },
  ...
]
```
