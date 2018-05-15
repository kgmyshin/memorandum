## Basic

https://redux.js.org/basics

### [Actions](https://redux.js.org/basics/actions)

- `action` は `application` から `store` に送るデータ
- `action` は `plain javascript object`
- `action` は 何を行ったのかを示す `type` プロパティを持たなければならない
- 可能な限り `action` のデータの粒度は小さい方が良い

#### [Action Creators](https://redux.js.org/basics/actions#action-creators)

- `action creator` はその名の通り `action` を作る関数
- `redux` では `action creator` は単純に `action` を返却するだけ
  - これによってテストしやすい
- `flux` では下記のように、 `dispatch` も行うことがあるが、 `redux` ではこれは **しない**

```
function addTodoWithDispatch(text) {
  const action = {
    type: ADD_TODO,
    text
  }
  dispatch(action)
}
```

- `redux` では `dispatch` メソッドを呼ぶ
- また、 `bound action creator` を用意することもある

```
const boundAddTodo = text => dispatch(addTodo(text))
const boundCompleteTodo = index => dispatch(completeTodo(index))
```

### [Reducers](https://redux.js.org/basics/reducers)

- `reducers` は送信された `action` に応じて、 `application` の状態がどう変化するかを指定する
  - `action` は **何が起きたか**
  - `reducer` は **どうapplicationの状態を変えるか**

#### [Designing the State Shape](https://redux.js.org/basics/reducers#designing-the-state-shape)

- `redux` では `application state` は一つのオブジェクト
- コードを書く前にどういう形になるか考えてみると良い

#### [Handling Actions](https://redux.js.org/basics/reducers#handling-actions)

- `reducer` は `previous state` と `action` を受け取って `new state` を返す純粋関数
- `reducer` を純粋関数に保つことがキモ。下記のことは **ダメ。ゼッタイ。**
  - 引数の内容を変更する
  - APIコールなどの副作用を行う
  - `Date.now()` や `Math.random()` などの非純粋関数を呼ぶ

#### [Splitting Reducers](https://redux.js.org/basics/reducers#splitting-reducers)

- `state` の更新対象なプロパティごとに関数を作ってわけていくアプローチを、 `reducer composition`と呼ぶ。（そしてこれは `redux` をやる上で基礎的なところになる)
- sample

```
function todos(state = [], action) {
  switch (action.type) {
    case ADD_TODO:
      return [
        ...state,
        {
          text: action.text,
          completed: false
        }
      ]
    case TOGGLE_TODO:
      return state.map((todo, index) => {
        if (index === action.index) {
          return Object.assign({}, todo, {
            completed: !todo.completed
          })
        }
        return todo
      })
    default:
      return state
  }
}
​
function visibilityFilter(state = SHOW_ALL, action) {
  switch (action.type) {
    case SET_VISIBILITY_FILTER:
      return action.filter
    default:
      return state
  }
}
​
function todoApp(state = {}, action) {
  return {
    visibilityFilter: visibilityFilter(state.visibilityFilter, action),
    todos: todos(state.todos, action)
  }
}
```

- `redux` は `combineReducers()` とうメソッドを用意している

```
const todoApp = combineReducers({
  visibilityFilter,
  todos
})
```

### [Store](https://redux.js.org/basics/store)

- `store` は `action` と `reducer` を結びつけるオブジェクト
- 下記がルール
  - `application state` を持っている
  - `getState()` で `state` にアクセスできる
  - `dispatch(action)` で `state` の更新ができる
  - `subscribe(listener)` で `listener` の登録ができる

### [Data Flow](https://redux.js.org/basics/data-flow)

- `redux` は **厳格に単一方向のデータフロー**
- 全てのデータが同じライフサイクルパターンになる
- ロジックがわかりやすい
- データの正規化が行われやすい

- どんな `redux` アプリも下記のライフサイクルになる
  1. `store.dispatch(action)` で発火
  2. `store` が `reducer` の関数を呼ぶ
  3. `root reducer` が複数の `reducer` のアウトプットを結合する
  4. `store` が `root reducer` の結果を保存する

## Advanced

### [Async Actions](https://redux.js.org/advanced/async-actions)

#### [Actions](https://redux.js.org/advanced/async-actions#actions)

- 非同期APIを呼び出すとき、開始した瞬間と、結果を受け取った瞬間の2つの重要な瞬間がある
- これらによって少なくとも3つの `action` を用意する必要がある
  - リクエスト開始の `action`
  - リクエストが完了して成功した時の `action`
  - リクエストが完了して失敗した時の `action`

#### [Async Action Creators](https://redux.js.org/advanced/async-actions#async-action-creators)

- 同期な `action` と `network request` をどう共存させるか => `middlware` を使おう

### [Async Flow](https://redux.js.org/advanced/async-flow)

- `applyMiddleware()` を用いて `createStore()` を拡張する
- `middleware` は `store` の `dispatch()` をラップして、 関数や `Promise` などの `action` 以外のものを `dispatch` する
- `middleware` は `dispatch` したものを、チェーンの次の `middleware` に渡す


### [Middleware](https://redux.js.org/advanced/middleware)

- `middleware` は `action` が `dispatch` されてから、 `reducer` に到達するまでの間に、3rd-partyの拡張を提供する
- `applyMiddleware` で複数の `middleware` が `store#dispatch` 時に `action` が `middleware` に届くようになる
