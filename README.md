# useStateObject

Have you ever come across a react component that uses many useState's declarations?

This library aims to solve that exactly.

Example:

here's the state of the component in general:

```typescript
type State = {
  name: string;
  age: number;
  male: boolean;
  address: {
    country: string;
    city: string;
    street: string;
    zipCode: number;
  };
};
```

_Old_

```typescript
const [name, setName] = useState("Erik");
const [age, setAge] = useState(27);
const [male, setMale] = useState(true);
const [address, setAddress] = useState({
  country: "Russia",
  city: "San Petersburg",
  street: "St. NewYork",
  zipCode: 83432,
});
```

_New_

```typescript
const { actions, state } = useStateObject({
  name: "Erik",
  age: 27,
  male: true,
  address: {
    country: "Russia",
    city: "San Petersburg",
    street: "St. NewYork",
    zipCode: 83432,
  },
});

/**
 * state = {
 *   name, -> string
 *   age, -> number
 *   male, -> boolean,
 *   address, -> object
 * }
 * actions = {
 *   setName, -> (value: string) => void
 *   setAge, -> (value: number) => void
 *   setAddress, -> (value: object) => void
 *   setMale, -> (value: boolean) => void
 * }
 */
```
