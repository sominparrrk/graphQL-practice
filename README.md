# GraphQL-Practice

## query (GET)

### Get team info

```graphql
query {
  teams {
    id
    manager
    office
    extension_number
    mascot
    cleaning_duty
    project
  }
}
```

### Get selected team info

- Selected elements

```graphql
query {
  teams {
    manager
    office
  }
}
```

- Selected teams

```graphql
query {
  team(id: 1) {
    manager
    office
  }
}
```

### Get team info & members info of that team

```graphql
query {
  team(id: 1) {
    manager
    office
    members {
      first_name
      last_name
    }
  }
}
```

- Results

```json
{
  "data": {
    "team": {
      "manager": "Mandy Warren",
      "office": "101A",
      "members": [
        {
          "first_name": "Nathan",
          "last_name": "Jenkins"
        },
        {
          "first_name": "Isabella",
          "last_name": "Martin"
        },
        {
          "first_name": "Kate",
          "last_name": "Owen"
        }
      ]
    }
  }
}
```

### Get team info & roles info

```graphql
query {
  teams {
    manager
    office
    mascot
  }
  roles {
    id
    requirement
  }
}
```

- Results

```json
{
  "data": {
    "teams": [
      {
        "manager": "Mandy Warren",
        "office": "101A",
        "mascot": "Panda"
      },
      {
        "manager": "Stewart Grant",
        "office": "101B",
        "mascot": "Tadpole"
      }
    ],
    "roles": [
      {
        "id": "developer",
        "requirement": "computer science degree"
      },
      {
        "id": "designer",
        "requirement": "graphic design certificate"
      },
      {
        "id": "planner",
        "requirement": "portfolio"
      }
    ]
  }
}
```

## mutation (POST, PUT, DELETE)

### Add new team (POST)

Should mention the key of the updated elements

```graphql
mutation {
  postTeam(
    input: {
      manager: "Somin"
      office: "Manchester"
      extension_number: "#9832"
      mascot: "Turtle"
      cleaning_duty: "Monday"
      project: "GraphQL"
    }
  ) {
    manager
    office
    extension_number
    mascot
    cleaning_duty
    project
  }
}
```

### Update selected team (PUT)

```graphql
mutation {
  editTeam(
    id: 2
    input: {
      manager: "Somin Park"
      office: "Stockport"
      extension_number: "9832"
      mascot: "Monkeys"
      cleaning_duty: "Friday"
      project: "Arctic"
    }
  ) {
    id
    manager
    office
    extension_number
    mascot
    cleaning_duty
    project
  }
}
```

### Delete selected team (DELETE)

```graphql
mutation {
  deleteTeam(id: 3) {
    id
    manager
    office
    extension_number
    mascot
    cleaning_duty
    project
  }
}
```

## Apollo

### ApolloClient

Similar role to axios. Useful handling cache.

### InMemoryCache

Prevents re-request and handle cache when once GraphQL Client got the data

### useQuery

- loading
- error
- data
