# Data Mapping: DADATA Service to Online Store Order POST Method

## Mapping Table

| Target Field (`myshop.ru/order/`) | Source Field (DADATA) | Transformation Logic |
| :--- | :--- | :--- |
| `delivery.address.index` | `postal_code` | Direct mapping. |
| `delivery.address.district` | `region_with_type`, `area_with_type` | If `area_with_type` is not null, concatenate: `region_with_type + ", " + area_with_type`. Otherwise, use `region_with_type` only. |
| `delivery.address.city` | `city_with_type` | Direct mapping. |
| `delivery.address.village` | `settlement_with_type` | Direct mapping. |
| `delivery.address.street` | `street_with_type` | Direct mapping. |
| `delivery.address.house` | `house` | Direct mapping. |
| `delivery.address.structure` | `block` | Direct mapping. |
| `delivery.address.flat` | `flat` | Direct mapping. |

## Extended Object for Verification Failure Handling

**Requirement:** Ensure the order can be processed even if the DADATA service fails or the address is invalid. The system must know whether verification was successful and retain the raw user input.

**Added Fields:**

| Field Name | Type | Description |
| :--- | :--- | :--- |
| `delivery.addressChecked` | `boolean` | Indicates whether DADATA successfully verified the address (`data.fias_level` was 8 or 9). |
| `delivery.rawAddressString` | `string` | The original address string entered by the user. Populated only if verification fails. |

**Filling Logic:**
- **Success Condition:** `data.fias_level` equals `8` or `9`.
  - Set `addressChecked = true`.
  - Set `rawAddressString = null`.
  - Populate the nested `address` object using the mapping table above.
- **Failure Condition:** Service unavailable, malformed address, or `data.fias_level < 8`.
  - Set `addressChecked = false`.
  - Set `rawAddressString` to the exact user input.
  - Set all fields inside the `address` object to `null`.

*Refer to the `/json-examples` folder for sample payloads.*
