# Record Selected

**Overview:**\
This channel is focused on the selection of records within the application. It's used to handle and respond to changes in the selection of records by the user.

**Usage:**\
Primarily used to update the UI or trigger actions based on the selection of a record, ensuring that the application remains responsive to user selections.

**Parameters:**

* **record**: Data representing the record that was selected or changed.

**Note:**\
The source XML contains a commented-out `sender` field. It is not emitted on the channel payload — do not rely on it.

**Channel Name (for import):**

```javascript
import RECORD_SELECTED_CHANNEL from "@salesforce/messageChannel/RDraw__Record_Selected__c";
```

**Publisher Components:**

* standalone\_DataTable

**Subscriber Components:**

* canvas3D
* canvas2D

\
