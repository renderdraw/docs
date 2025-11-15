# Advanced Metadata Relationships

There are scenarios where it makes sense to render based on another record's setup. A good example of this is rendering a 3D model associated with an asset, whose 3D CAD file is linked to a product. We can re-utilize drawings multiple times across all use cases in the Salesforce ecosystem based on advanced relationships that are setup inside the RenderDraw Relationships metadata.&#x20;

#### Parent-Child Relationships

There are two main relationships to consider, in the scenario above, the child record would be an Asset. In that case, we want to take a look at the parent relationship for reference to the related setup scene. Additional attributes can be applied on top of the base rendered setting, such as colors, backgrounds or events. For this type of relationship, take a look at [parent-child-relationships.md](parent-child-relationships.md "mention")

#### Child Lookups

On selection of an item, often times the subcomponents of a given 3D assembly are represented by a different object in the Salesforce system, or we need to do some matching on a given object's field data to the underlying 3D component name. To achieve this, we need to setup [child-lookup.md](child-lookup.md "mention") fields on the relationship metadata record.&#x20;
