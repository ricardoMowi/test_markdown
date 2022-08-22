# Manejo de estado con contexto

## Comunicación
Para un mejor uso de los estados con contexto debes implementar interfaces de comunicación, lo que hace más legible la implementación y más sencilla de usar.

Implementación useContext + useState.
```js
// modules/exampleModule/contexts/userContext.js

import React, { useMemo, useState, useEffect } from "react";

const UserContext = React.createContext();

export function UserProvider (props) {
  const [user, setUser] =  setState({ name: '' });

  useEffect(() => {
    ...
    // call from service and update setUser
  }, []);

  const userState = useMemo(() => ({
    user
  }), [user]);

  return <UserContext.Provider value={userState } {...props} />
}

export function useUserContext() {
  const context = React.useContext(UserContext );
  if (!context) {
    throw new Error('UserContext provider is required')
  }
  return context;
}
```

Uso
```
// modules/exampleModule/pages/profile.jsx


```

Implementación useContext + useReducer, como alternativa similar a redux.

```js

import React, { useReducer } from 'react';

const todos = [
    {
        title: 'Get milk',
        completed: true,
    },
    {
        title: 'Make YouTube video',
        completed: false,
    },
    {
        title: 'Write blog post',
        completed: false,
    },
];

const initialState = {
    username: '',
    password: '',
    isLoading: false,
    error: '',
    isLoggedIn: false,
    todos,
};

const loginReducer = (state, action) => {
    switch (action.type) {
        case 'field': {
            return { ...state, [action.fieldName]: action.payload }
        }
        case 'login': {
            return { ...state, eror: '', isLoading: true }
        }
        case 'success': {
            return { ...state, isLoggedIn: true, isLoading: false, username: '', password: '' }
        }
        case 'error': {
            return {
                ...state, error: 'Incorrect username or password!', isLoggedIn: false,
                isLoading: false, username: '', password: ''
            }
        }
        case 'logOut': {
            return { ...state, isLoggedIn: false }
        }
        case 'toggleTodoCompleted': {
            const todos = JSON.parse(JSON.stringify(state.todos));
            const newTodos = todos.map((item) => {
                if (item.title === action.payload) item.completed = !item.completed
                return item;
            });
            return { ...state, todos: newTodos };
        }
        default:
            return;
    }
}

const StateLoginContext = React.createContext();
const DispatchLoginContext = React.createContext();

export const LoginProvider = (props) => {
    const [state, dispatch] = useReducer(loginReducer, initialState);

    return (
        <DispatchLoginContext.Provider value={dispatch}>
            <StateLoginContext.Provider value={state}>
                {props.children}
            </StateLoginContext.Provider>
        </DispatchLoginContext.Provider>
    );
}

export const useStateLoginContext = () => React.useContext(StateLoginContext);
export const useDispatchLoginContext = () => React.useContext(DispatchLoginContext);

export default LoginProvider;

```
