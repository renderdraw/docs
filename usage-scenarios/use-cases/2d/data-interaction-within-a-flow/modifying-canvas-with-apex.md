# Modifying Canvas with APEX



```
public with sharing class Test_CanvasTransform { public Test_CanvasTransform() { }
@InvocableMethod
public static List<RDraw.Canvas> getTestCanvas() {
	try {
		RDraw.Canvas can = new RDraw.Canvas();
		can.id = 'abc123';
		can.name = 'Test Canvas';
		can.placedDroppableAreas = new List<RDraw.DroppableArea>();
		for (Integer i = 0; i < 4; i++) {
			RDraw.DroppableArea da = new RDraw.DroppableArea();
			da.id = 'da' + i;
			da.name = 'Droppable Area ' + i;
			da.sortingEnabled = true;
			da.sortingDirection = 'end'; 
			da.recordId = '01tDP00000AO113YAD';
			da.draggableItems = new List<RDraw.BaseCanvasItem>();
			for (Integer j = 0; j < 5; j++) {
				RDraw.BaseCanvasItem bci = new RDraw.BaseCanvasItem();
				String recordId = Math.Mod(j, 2) == 0 ? '01tDP00000APsFIYA1' : '01tDP00000APsFcYAL';
				bci.id = 'bci' + j;
				bci.name = 'Base Canvas Item ' + j;
				bci.recordId = recordId;
				da.draggableItems.add(bci);
			}
			can.placedDroppableAreas.add(da);
		}

		List<RDraw.Canvas> canList = new List<RDraw.Canvas>();
		canList.add(can);
		return canList;
	} catch (Exception e) {
		throw new AuraHandledException(e.getMessage());
	}
}
```

}
