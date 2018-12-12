+++
date = 2018-06-08T16:00:00+09:00
title = "ReactRedux.connect の mergeProps と型定義"
thumbnail = "images/redux.png"
tags = ["JavaScript", "React", "Redux", "TypeScript", "Typing"]
categories = ["Engineering"]
# ["Tech", "Engineering", "Life", "Poem", "DevEnv", "Otaku", "Career"]
+++

## ReactRedux の connect の型定義

型定義無しの場合は以下のように書く前提とする。

```js
export default connect(mapStateToProps, mapDispatchToProps)(MyComponent)
```

型定義を付ける場合は Generics 記法で以下のように書く。

```js
export default connect<StateProps, DispatchProps, OwnProps>(
  mapStateProps,
  mapDispatchToProps
)(MyComponent)
```

この記法により、 `mapStateToProps` `DispatchProps` により生成される Props の型、 `OwnProps`(`<MyComponent />` に渡す Props) の型がそれぞれ定義されるため、Component 記述の際に渡される Props に対して型制約を付けることができる。

しかし `mergeProps` を使用する場合、上記の型定義だと壊れてしまう。

## mergeProps 使う場合の型定義

結論としては以下の通りになる。

`type Props = StateProps & DispatchProps & OwnProps` である。

```js
export default connect<StateProps, DispatchProps, OwnProps, Props>(
  mapStateProps,
  mapDispatchToProps,
  mergeProps
)(MyComponent)
```

mergeProps で dispatch をする場合は以下になるかと思われる。

```js
export default connect<StateProps, {}, OwnProps, Props>(
  mapStateProps,
  (dispatch: Dispatch) => ({ dispatch }),
  mergeProps
)(MyComponent)
```

connect の Generics 引数(？)は型定義を見ると 4 つまで取れることがわかる。

```js
export interface Connect {
  (): InferableComponentEnhancer<DispatchProp>;

  <TStateProps = {}, no_dispatch = {}, TOwnProps = {}, State = {}>(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>
  ): InferableComponentEnhancerWithProps<TStateProps & DispatchProp, TOwnProps>;

  <no_state = {}, TDispatchProps = {}, TOwnProps = {}>(
    mapStateToProps: null | undefined,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>
  ): InferableComponentEnhancerWithProps<TDispatchProps, TOwnProps>;

  <TStateProps = {}, TDispatchProps = {}, TOwnProps = {}, State = {}>(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>
  ): InferableComponentEnhancerWithProps<
    TStateProps & TDispatchProps,
    TOwnProps
  >;

  <
    TStateProps = {},
    no_dispatch = {},
    TOwnProps = {},
    TMergedProps = {},
    State = {}
  >(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: null | undefined,
    mergeProps: MergeProps<TStateProps, undefined, TOwnProps, TMergedProps>
  ): InferableComponentEnhancerWithProps<TMergedProps, TOwnProps>;

  <no_state = {}, TDispatchProps = {}, TOwnProps = {}, TMergedProps = {}>(
    mapStateToProps: null | undefined,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>,
    mergeProps: MergeProps<undefined, TDispatchProps, TOwnProps, TMergedProps>
  ): InferableComponentEnhancerWithProps<TMergedProps, TOwnProps>;

  <no_state = {}, no_dispatch = {}, TOwnProps = {}, TMergedProps = {}>(
    mapStateToProps: null | undefined,
    mapDispatchToProps: null | undefined,
    mergeProps: MergeProps<undefined, undefined, TOwnProps, TMergedProps>
  ): InferableComponentEnhancerWithProps<TMergedProps, TOwnProps>;

  <
    TStateProps = {},
    TDispatchProps = {},
    TOwnProps = {},
    TMergedProps = {},
    State = {}
  >(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>,
    mergeProps: MergeProps<TStateProps, TDispatchProps, TOwnProps, TMergedProps>
  ): InferableComponentEnhancerWithProps<TMergedProps, TOwnProps>;

  <TStateProps = {}, no_dispatch = {}, TOwnProps = {}, State = {}>(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: null | undefined,
    mergeProps: null | undefined,
    options: Options<State, TStateProps, TOwnProps>
  ): InferableComponentEnhancerWithProps<DispatchProp & TStateProps, TOwnProps>;

  <TStateProps = {}, TDispatchProps = {}, TOwnProps = {}>(
    mapStateToProps: null | undefined,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>,
    mergeProps: null | undefined,
    options: Options<{}, TStateProps, TOwnProps>
  ): InferableComponentEnhancerWithProps<TDispatchProps, TOwnProps>;

  <TStateProps = {}, TDispatchProps = {}, TOwnProps = {}, State = {}>(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>,
    mergeProps: null | undefined,
    options: Options<State, TStateProps, TOwnProps>
  ): InferableComponentEnhancerWithProps<
    TStateProps & TDispatchProps,
    TOwnProps
  >;

  <
    TStateProps = {},
    TDispatchProps = {},
    TOwnProps = {},
    TMergedProps = {},
    State = {}
  >(
    mapStateToProps: MapStateToPropsParam<TStateProps, TOwnProps, State>,
    mapDispatchToProps: MapDispatchToPropsParam<TDispatchProps, TOwnProps>,
    mergeProps: MergeProps<
      TStateProps,
      TDispatchProps,
      TOwnProps,
      TMergedProps
    >,
    options: Options<State, TStateProps, TOwnProps, TMergedProps>
  ): InferableComponentEnhancerWithProps<TMergedProps, TOwnProps>;
}
```

あまり説明がないので、複雑だが型定義を読む方が早い。

オーバーライドしているので WebStorm でも型候補が出ないのが惜しいところである。
