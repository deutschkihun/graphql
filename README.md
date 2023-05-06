# graphql

## Try this queries in first project (1-apollo-server)

```tsx
query {
    equipments {
        id
        used_by
        count
        new_or_used
    }
}
```

```tsx
query {
team(id: 1) {
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

### delete mutation

```tsx
mutation {
  deleteEquipment(id: "notebook") {
    id
    used_by
    count
    new_or_used
  }
}
```

### insert mutation

```tsx
mutation {
  insertEquipment (
    id: "laptop",
    used_by: "developer",
    count: 17,
    new_or_used: "new"
  ) {
    id
    used_by
    count
    new_or_used
  }
}
```

### edit mutation

```tsx
mutation {
  editEquipment (
    id: "pen tablet",
    new_or_used: "new",
    count: 30,
    used_by: "designer"
  ) {
    id
    new_or_used
    count
    used_by
  }
}
```

## Try this queries in second project (2-modularized-apollo-server)

```tsx
query {
    equipmentAdvs {
        id
        used_by
        count
        use_rate
        is_new
    }
}
```

```tsx
query {
  equipments {
    id
    used_by
    count
    new_or_used
  }
	equipmentAdvs {
    id
    used_by
    count
    use_rate
    is_new
  }
}
```

```tsx
query {
	equipmentAdvs {
    id
    used_by
    count
    use_rate
    is_new
    users
  }
}
```

### union

```tsx
query {
  givens {
    __typename
    ... on Equipment {
      id
      used_by
      count
      new_or_used
    }
    ... on Supply {
      id
      team
    }
  }
}
```

### interface

```tsx
query {
  equipments {
    id
    used_by
    count
    new_or_used
  }
  softwares {
    id
    used_by
    description
    developed_by
  }
}
```

### union and interface

```tsx
query {
  people {
    id
    first_name
    last_name
    givens {
        __typename
    	... on Equipment {
      	id
      	used_by
      	count
      	new_or_used
    	}
    	... on Supply {
      	id
      	team
    	}
  	}
    tools {
      __typename
      ... on Equipment {
        id
        used_by
        count
        new_or_used
      }
      ... on Software {
        id
        used_by
        description
        developed_by
      }
    }
  }
}
```

### condition

```tsx
query {
  peopleFiltered (
    team: 1
    blood_type: B
    from: "Texas"
  ) {
    id
    first_name
    last_name
    sex
    blood_type
    serve_years
    role
    team
    from
  }
}
```

### pagination

```tsx
query {
  peopleFiltered (
    team: 1
    blood_type: B
    from: "Texas"
  ) {
    id
    first_name
    last_name
    sex
    blood_type
    serve_years
    role
    team
    from
  }
}
```

### rename

```tsx
query {
  badGuys: peopleFiltered(sex: male, blood_type: B) {
    first_name
    last_name
    sex
    blood_type
  }
  newYorkers: peopleFiltered(from: "New York") {
    first_name
    last_name
    from
  }
}
```

### input type

```tsx
mutation {
  postPerson(input: {
    first_name: "Hanna"
    last_name: "Kim"
    sex: female
    blood_type: O
    serve_years: 3
    role: developer
    team: 1
    from: "Pusan"
  }) {
    id
    first_name
    last_name
    sex
    blood_type
    role
    team
    from
  }
}
```

## Fragment (apollo-client 참고)

여러 쿼리에 사용될 수 있는, 재사용 가능한 필드셋
중복을 줄임으로써 전체 코드를 간소화
