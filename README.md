## GraphQL Client

GraphQL Apollo client for Hacker new clone.

### Client Side Features

* Authentication
* Queries, Mutations
* Filtering
* Pagination
* Routing

### Client Side Auth Mutation 

```javascript
// sign up mutation
const SIGN_UP_MUTATION = gql`
  mutation SignupMutation($email: String!, $password: String!, $name: String!) {
    signup(email: $email, password: $password, name: $name) {
      token
    }
  }
`;

// login mutation
const LOGIN_MUTATION = gql`
  mutation LoginMutation($email: String!, $password: String!) {
    login(email: $email, password: $password) {
      token
    }
  }
`;
```

```javascript
// useMutation hooks
const Login = () => {
  //..

  const [login] = useMutation(LOGIN_MUTATION, {
      variables: {
          email: formState.email,
          password: formState.password
      },
      onCompleted: ({login}) => {
          localStorage.setItem(AUTH_TOKEN, login.token);
          history.push('/');
      }
  })

  const [signup] = useMutation(SIGN_UP_MUTATION, {
    variables: {
      name: formState.name,
      email: formState.email,
      password: formState.password
    },
    onCompleted: ({ signup }) => {
      localStorage.setItem(AUTH_TOKEN, signup.token);
      history.push('/');
    }
  });

  //..

  return (
    <>
    </>
};

export default Login;
```

### Credits

 The inspiration for this quick, fun project was the need to revise GraphQL with all the fundamentals needed to build real world applications. Thanks to [How to GraphQL](https://www.howtographql.com/), their approach is better than most books
 or blog posts you'll read on the subject.