# Ory Keto Tests

## Run Container

    docker-compose up

## Permissions

View only access for finance department

    reports:finance#view@(groups:finance#member)

View only access for community department

    reports:community#view@(groups:community#member)

View only access for marketing department

    reports:marketing#view@(groups:marketing#member)

Edit access for admin group

```
reports:finance#edit@(groups:admin#member)
reports:community#edit@(groups:admin#member)
reports:marketing#edit@(groups:admin#member)
reports:finance#view@(groups:admin#member)
reports:community#view@(groups:admin#member)
reports:marketing#view@(groups:admin#member)
```

## Relationships

```
groups:finance#member@Lila
groups:community#member@Dilan
groups:marketing#member@Hadley
groups:admin#member@Neel
```

## Checks

```
keto check Dilan view reports finance
keto check Dilan view reports community
keto check Dilan edit reports community
```

## Display all objects a user has access to

Get all groups for Dilan

    keto relation-tuple get groups --subject-id=Dilan --relation=member --format json-pretty

Get permissions to objects for marketing group

    keto relation-tuple get reports --subject-set="groups:marketing#member" --format json-pretty

## Display who has access to an object

    keto expand view reports marketing --format json-pretty --max-depth 3

## List all employees of company

    keto expand employee orgs company-a --format json-pretty --max-depth 3

## Ceck if user can view other user

    keto check Dilan view users Lila
