# redux useSelector and useDispatch

- `useSelector` is the hooks alternative for `mapStateToProps`
- `useDispatch` is the hooks alternative for `mapDispatchToProps`

## Using the `connect` Higher Order Component

    import { addCount } from "./store/counter/actions";

    const Count = ({ count, addCount }) => {
        return (
            <main>
            <div>Count: {count}</div>
            <button onClick={addCount}>Add to count</button>
            </main>
        );
    };

    const mapStateToProps = state => ({
        count: state.counter.count
    });

    const mapDispatchToProps = { addCount };

    export default connect(mapStateToProps, mapDispatchToProps)(Count);

## Using react-redux hooks

    import { addCount } from "./store/counter/actions";

    export const Count = () => {
        const count = useSelector(state => state.counter.count);
        const dispatch = useDispatch();

        return (
            <main>
            <div>Count: {count}</div>
            <button onClick={() => dispatch(addCount())}>Add to count</button>
            </main>
        );
    };

[source](https://thoughtbot.com/blog/using-redux-with-react-hooks)
