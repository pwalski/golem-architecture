## Turbogeth managed service

This article contains examples of Demands & Offers which cover the a Managed Service example (turbogeth).

Compared to Standards v0.6.0, the sample includes a couple of extensions:

### Perpetual Agreement

No `golem.srv.comp.expiration` property specified on the Demand side indicates no expected Agreement end date.

### "Eth" Application Namespace

Any "Ethereum-specific" properties would be maintained in this namespace. This sample includes:

`golem.srv.app.eth.rpc-port` - Indication of RPC endpoint port exposed by the provisioned Geth service.

### Managed Turbogeth runtime

`golem.runtime.name=turbogeth-managed` - Indicated a Managed Turbogeth service to be launched

### PAYU payment scheme enhancements

Two negotiable properties to determine Debit Note and Payment intervals:

`golem.com.scheme.payu.debit-note-interval-sec?` - Debit Notes issue interval
`golem.com.scheme.payu.payment-interval-sec?` - Expects Payments to be made within specific interval after Debit Note is issued

### Sample Offer

```
"properties": {
    "golem.com.payment.platform.erc20-mainnet-glm.address": "0x128282ae0ba38689f215cb3cc278008620f50253",
    "golem.com.payment.platform.zksync-mainnet-glm.address": "0x128282ae0ba38689f215cb3cc278008620f50253",
    "golem.com.pricing.model": "linear",
    "golem.com.pricing.model.linear.coeffs": [
        0.0002777777777777778,
        0.001388888888888889,
        0.0
    ],
    "golem.com.scheme": "payu",
    "golem.com.scheme.payu.debit-note-interval-sec?": 60, // Debit Notes issues every minute
    "golem.com.scheme.payu.payment-interval-sec?": 360,  // Expects Payments to be made within 5 minutes of Debit Note issue 
    "golem.com.usage.vector": [
        "golem.usage.duration_sec",
        "golem.usage.cpu_sec"
    ],
    "golem.inf.cpu.cores": 3,
    "golem.inf.mem.gib": 16,
    "golem.inf.storage.gib": 2048,
    "golem.node.id.name": "provider_2",
    "golem.runtime.name": "turbogeth-managed",  // indicates the "managed"/"wrapped" turbogeth ExeUnit
    "golem.runtime.version": "0.2.1",
    },
},
"constraints": "()"
```

### Sample Demand

```
"properties": {
    "golem.node.id.name": "test1",
    "golem.srv.app.eth.rpc-port": 9001,  // Indicates requested RPC endpoint port number
},
constraints: "(&
    (golem.runtime.name=turbogeth-managed)
    (golem.inf.mem.gib>=16)
    (golem.inf.storage.gib>=1024)
    (golem.com.pricing.model=linear)
    )"
```
