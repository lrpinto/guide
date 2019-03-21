---
title: Use Middleware to Handle Asynchronous Actions
---
## Use Middleware to Handle Asynchronous Actions

There are two parts to this challenge.

1. Dispatch the REQUESTING_DATA action before simulated API call.
2. Dispatch the RECEIVED_DATA action after you receive the sample data returned by the simulated API call, passing this data as parameter to the action creator.

### Step 1. Dispatch REQUESTING_DATA.

Dispatch the action created by `requestingData()` to the Redux store.

```react.js
store.dispatch(requestingData());
```

### Step 2. Dispatch RECEIVED_DATA.

Dispatch the action created by `receivedData(data)` to the Redux store, passing as parameter the sample data received from the simulated API call.

```react.js
store.dispatch(receivedData(data));
```

### Solution

```react.js
const handleAsync = () => {
  return function(dispatch) {
    // dispatch request action here
    store.dispatch(requestingData())
    setTimeout(function() {
      let data = {
        users: ['Jeff', 'William', 'Alice']
      }
      // dispatch received data action here
      store.dispatch(receivedData(data))
    }, 2500);
  }
};
```

All done!
