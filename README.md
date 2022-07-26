# Jolt
Jolt issue on array output

Need help with output array values.

Input :
{
  "fPay": {
    "tap": "Green"
  },
  "gPay": {
    "swipe": "RED"
    
  }
}

Expected output :
tap should be populated with gPay swipe value , and when null or empty should take fPay tap value

Spec in use:
[

  {
    "operation": "modify-default-beta",
    "spec": {
      "fPay": {
        "tap": null
      }
    }
  },

  {
    "operation": "shift",
    "spec": {
      "gPay": {
        "swipe": "tap"
      },
      "fPay": {
        "tap": "tap"
      }
    }
  }
]

Current output :
{
  "tap" : [ "Green", "Red" ]
}

I need to just get the value of Gpay as priority and when null should get fPay value, NO ARRAY should be displayed in output
Note : used cardinality, but when fPay value is ignored when gPay is null or empty.
