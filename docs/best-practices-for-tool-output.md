# Best practices for tool output


## 1. Outputs
The outputs should not contain a human written like sentences. Becuase this is an API function response, it's more expected to have it more concise, straightforward, key-value paired, `number`/`enum` oriented.

- Thus an output like this is not good:

```json
    {
        "message": "The item with ID 342 is updated successfully."
    }
```

- Instead, the below is better:

```json
    {
        "status": "OK",
        "success": true,
        "action": "update",
        "data": {
            "item_id": 342
        }
    }
```

## 2. Error messages
In case there's an error, the error messages should be descriptive and possibly it might contain a statement how to recover from failure.

Error messages or feedback should provide specific corrective actions rather than just highlighting issues.


- The below error message is not corrective:

```json
    {
        "status": 500,
        "message": "Internal server error"
    }
```


- Instead below is a better and corrective error message:

```json
    {
        "status": "500",
        "message": "Internal server error",
        "error": "Item ID is None!"
    }
```

> Here the model can understand that the reason is to have Item ID to be None, and so it knows how to resolve it.