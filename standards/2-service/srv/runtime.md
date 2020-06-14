# Computation Runtime Specifiation 
Specification of ExeUnit/Runtime to host the resources provided.

## Common Properties

(Not applicable)
  
## Specific Properties

## `golem.srv.runtime.name : String` 
Indicates the ExeUnit/Runtime required/provided. 
### Value enum
| Value      | Description                                        |
| ---------- | -------------------------------------------------- |
| "wasmtime" | Golem Factory's WASI runtime (based on `wasmtime`) |
|            |                                                    |

### **Examples**

* `golem.srv.runtime.name="wasmtime"` - declares that `wasmtime` is available as runtime on the provider node.
  
## `golem.srv.runtime.version : Version` 
Version of the ExeUnit/Runtime required/provided.

### **Examples**

* `golem.srv.runtime.version="0.0.0"` - declares runtime version 0.0.0.

