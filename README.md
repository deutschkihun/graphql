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

여러 쿼리에 사용될 수 있는, 재사용 가능한 필드셋
중복을 줄임으로써 전체 코드를 간소화
