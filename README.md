# Understanding PIM

> Bizzkit Academy - last edited March 13, 2023 (PIM version 21.49.1)

Bizzkit PIM is a Product Information Management (PIM) system designed specifically for e-commerce and tailored to the needs of omnichannel businesses, catering to both B2B and B2C companies. Developed in close cooperation with the industry, it ensures simple workflows and supports scalability while remaining fully customizable to match your unique business requirements and ambitions. There are no fixed data structures or predefined settings, allowing you to define everything according to your preferences. In this article, we provide a comprehensive overview of Bizzkit PIM's powerful features and demonstrate how it can elevate your e-commerce strategies while streamlining operations, ensuring product data consistency, and improving customer experiences.

Before looking into the different features of PIM lets start by looking at its key benefits:

- *** Feature-Rich UI: *** Bizzkit PIM offers an extensive and user-friendly interface that allows users to manage and maintain their product data with ease. 

- *** REST API: *** Bizzkit PIM offers a comprehensive REST API that serves as the foundation for developing e-commerce solutions. The API allows developers to access and manage data programmatically, ensuring seamless integration with other systems and providing the flexibility needed to create customized e-commerce solutions tailored to your business needs.

- *** Extensive Attribute System: *** One of the key strengths of Bizzkit PIM lies in its highly versatile attribute system. With numerous attribute types available, users can create very complex PIM models. This flexibility makes Bizzkit PIM an ideal solution for businesses in various industries, including those with intricate product catalogs. Additionally, the attribute system is employed across several aspects of PIM, such as hierarchies, global lists, bundles, and more, further enhancing its versatility and adaptability to different use cases.

- *** Internal and External Values: *** In PIM, attribute values are managed using a shadowing system, which stores both internal and external values for each attribute. This approach enables seamless integration with other systems, such as ERP, CRM, PLM, or pricing management systems, allowing for values to be owned and maintained by these systems while also providing the option to override them within the PIM.

- *** Segmentation System: *** With Bizzkit PIM's unique segmentation system, users can define attribute values based on different cultures, markets, channels, and devices. This powerful feature enables businesses to customize their product information for various target audiences.

- *** Scalability: *** Bizzkit PIM is designed to handle large-scale product catalogs, having been tested to accommodate up to 20 million products in an advanced model with multiple attributes. This ensures that as your business grows, your PIM system will continue to support your expanding product range without compromising performance or efficiency.

- *** Robust Permission System: ***  Bizzkit PIM's permission system allows admin users to have control over other users' access to specific features. This ensures that team members are granted appropriate permissions.

## The attribute system

Understanding the core concepts of fields, keys, and values is essential for utilizing Bizzkit PIM's attribute system effectively. Fields represent the basic building blocks of an attribute, each containing a unique key and a corresponding value or set of values.

Bizzkit PIM offers four overarching attribute types:

- Single field, single value: One field with a single associated value. 
- Single field, multiple values: One field with multiple associated values.
- Multiple fields (up to four), single value: Several fields, each with a single associated value.
- Multiple fields (up to four), multiple values: Several fields, each with multiple associated values.

This table provides an overview of the different attribute types used in the system, illustrating the relationship between fields and values in each category:

| Attribute Type                   | Field(s) | Value(s) |
|----------------------------------|----------|----------|
| Single field, single value       | 1        | 1        |
| Single field, multiple values    | 1        | Multiple |
| Multiple fields, single value    | Up to 4  | 1        |
| Multiple fields, multiple values | Up to 4  | Multiple |


These attribute types provide the flexibility needed to represent diverse product information within the PIM.

## Data types

Value types in Bizzkit PIM are diverse and encompass a wide range of data types, including:

- Simple types: Numbers, text, date/time, boolean values, etc.
- PIM entity references: References to internal PIM entities like products, brands, global lists, etc.
- Other Bizzkit types: Users, images from Bizzkit DAM, content pages from Bizzkit CMS.
- Calculated attribute: Advanced attribute type that derive their values based on formulas involving other attributes.

Attribute and data types makes Bizzkit PIM very powerful and enables users to represent and manage complex product data in a structured and efficient manner. 

!!! info 
    To better understand the different attribute types in Bizzkit PIM, let's explore an example involving external image(s) hosted on a web server:

    - Single field, single value: An attribute with a single field containing the URL (text value) of an external image. In this case, the attribute just represents the image location.

    | image_url                        |
    |----------------------------------|
    | https://example.com/image.jpg    |


    - Single field, multiple values: An attribute with a single field containing a list of URLs (text values) representing multiple external images. This type is widely used in PIM models.

    | image_url                       |
    |----------------------------------|
    | https://example.com/image1.jpg   |
    | https://example.com/image2.jpg   |
    | ...                              |


    - Multiple fields, single value: An attribute representing an external image with multiple fields, each containing a single value. In this case, the fields could include the URL (text), date the photo was taken (date/time), copyright notice (text), and a boolean indicating if the image is active or not.

    | image_url                        | date_taken | copyright_notice | is_active |
    |----------------------------------|------------|------------------|-----------|
    | https://example.com/image.jpg    | 2022-12-01 | Copyright 2022   | true      |


    - Multiple fields, multiple values: An attribute containing multiple fields, each representing a set of external images with various properties. 

    | image_url                        | date_taken | copyright_notice | is_active |
    |----------------------------------|------------|------------------|-----------|
    | https://example.com/image1.jpg   | 2022-12-01 | Copyright 2022   | true      |
    | https://example.com/image2.jpg   | 2022-12-02 | Copyright 2022   | false     |
    | ...                              | ...        | ...              | ...       |

    These examples illustrate the flexibility and versatility of Bizzkit PIM's attribute types when working with various product data configurations.

## Segmentation system

Bizzkit PIM's robust segmentation system enables businesses to manage their product information efficiently across various dimensions, such as translation culture, channel, market, and device. The most frequently used dimensions are translation culture and channel, which are crucial for catering to diverse audiences and distribution methods.

Attributes values in Bizzkit PIM can be associated with specific dimensions, allowing users to store and manage different text and numeric values for each combination. This feature is particularly useful for businesses operating in multiple countries or targeting various customer segments through different channels.

<figure markdown>
  ![](../../images/understanding/pim/dimensions.png){ width="500" }
  <figcaption>The four dimensions in PIM</figcaption>
</figure>

The PIM's user interface is designed to handle the segmentation system efficiently, providing users with an easy way to manage product data across for instance multiple translation cultures and channels. This intuitive approach ensures that users can work with segmented data effectively, streamlining the process of updating and maintaining product information across various dimensions.

As a simple example of segmented data could be a single field/single value "Description" attribute with a danish and an english value.

|Field name|Danish value|English value|
|-----------|--------------|---------|
|Value|Beskrivelse ...|Description ...|

<figure markdown>
  ![](../../images/understanding/pim/ui_dimension.png){ width="500" }
  <figcaption>Modifying a segmented attribute for a product in the UI</figcaption>
</figure> 

In addition to the UI, Bizzkit PIM's REST API supports segmentation by returning flattened data based on a specific segmentation. This functionality allows developers to access and manage segmented data programmatically.

## Internal and external values

In Bizzkit PIM, attribute values are managed using a unique shadowing system designed to store and maintain both internal and external values for each attribute. 

An external value is owned by an external system, such as an Enterprise Resource Planning (ERP) system or any other system, and cannot be updated directly in PIM. Instead, it must be overridden by adding internal values. This dual-value approach provides a level of flexibility that is particularly advantageous for organizations working with various external systems, such as ERP, Customer Relationship Management (CRM), Product Lifecycle Management (PLM), or Pricing Management systems. By having both internal and external values, PIM can effectively serve as a central hub for product information, streamlining the data flow between different systems and ensuring data consistency across the board.

<figure markdown>
  ![](../../images/understanding/pim/override.png){ width="500" }
  <figcaption>UI for selecting an override rule when creating an attribute</figcaption>
</figure> 

The shadowing system within PIM enables seamless integration with these external systems, allowing for values to be owned and maintained by them while also providing the option to override or supplement the data within PIM. 

There are different override behaviors that can be used to determine which value takes precedence. For example, suppose an e-commerce company has product descriptions stored in their ERP system, but they want to improve the text for specific products within PIM. The override behavior can be configured so that the PIM value takes precedence if it exists; otherwise, the system falls back to the ERP system's text. This capability is particularly useful for businesses that need to manage complex product catalogs, as it ensures that data can be updated and enriched from multiple sources without causing discrepancies or conflicts. Ultimately, the combination of internal and external values in Bizzkit PIM empowers organizations to create a more efficient and cohesive product information management process, ensuring that data is consistent, accurate, and up-to-date across all channels and systems.

## Maintaining attributes though the UI

In Bizzkit PIM, attributes can be managed efficiently through the Attributes tab. An attribute typically consists of a system name, display name, description, type (single or multiple value), and a confidentiality setting that determines if the attribute is part of the UI but not included in data returned from API calls.

When creating an attribute, you specify a template, called a configuration type, to help you set up the attribute structure more easily. The available configuration types include:

| Configuration Type | Description                                     |
|--------------------|-------------------------------------------------|
| Plain              | A simple attribute with single or multiple values.      |
| RectangularAreal   | A multi-field attribute with width and height fields.   |
| CuboidVolume       | A multi-field attribute with width, height, and length fields.|
| Range              | A multi-field attribute with 'from' and 'to' fields.|
| Quantified         | A multi-field attribute with item and quantity fields of any types.|
| Calculated         | An attribute based on a formula.|
| Unconstrained      | Used for manually configuring a multi-field attribute with up to 4 fields.|

After entering the basic information for an attribute, users can define an override rule to manage how PIM and externally owned values interact. There are four options to choose from: 

- Prefer PIM value and fallback to externally owned value
- Prefer externally owned value and fallback to PIM value
- Always use PIM value
- Always use externally owned value

These rules offer flexibility in determining the source of attribute values depending on the organization's specific requirements.

Next, users can enter details for the attribute's various fields, including the system name, display name, attribute type, or data source (such as a reference to a global list). 

Additionally, if needed, users can add predefined values to the attribute. By doing so, they can create a drop-down box where users are required to select from a list of predefined options, ensuring consistency and accuracy in the data entered.

Attributes can be organized and arranged within configurable attribute groups, which are displayed as tabs in the UI. This organization simplifies the process of locating attributes on the Product Detail Page (PDP) and ensures a more streamlined user experience.

## Global lists

In Bizzkit PIM, you can create a collection of predefined values, known as global lists, which can serve as data sources for fields in attributes. These global lists can represent various types of information, such as a list of colors or countries, streamlining the process of managing commonly used data.

For instance, imagine an e-commerce company that sells electronic products and wants to create a global list of manufacturers. This list could include well-known brands such as Apple, Samsung, Sony, and others. By establishing a global list for manufacturers, the company can efficiently manage product data and ensure consistency throughout their product catalog.

Additionally, Bizzkit PIM's attribute system allows users to add extra metadata to individual items within a global list. This capability enhances the granularity and flexibility of the information managed within the PIM, ensuring that each item can have its unique set of metadata for more precise and comprehensive data management.

For instance, consider a global list of colors. Each color, like WHITE, can have its own set of attributes with associated values. In this example, WHITE could have attributes for its RGB and HEX values, enabling systems to access and utilize these specific details.

<figure markdown>
  ![](../../images/understanding/pim/globallist.png){ width="500" }
  <figcaption>An example of a Color-global list - note the ability to add attributes</figcaption>
</figure> 

Global lists are not only useful for attributes but can also be employed as data sources for units used within PIM, such as measurement units (mm, cm, m, etc.). 

## Brands

In Bizzkit PIM, you can create a comprehensive list of brands that are part of your customer's offerings. Each brand on the list can include one or more attributes, allowing for the storage of any necessary metadata such as name, logo, and description.

For instance, in the clothing industry, brands like Tommy Hilfiger, Burberry, and Gucci could be included, while in the beverage sector, Coca-Cola, Pepsi, and Sprite might be listed. If required, you can also create brand hierarchies for a more organized structure. This flexibility ensures that all relevant brand information is easily accessible and maintained within the PIM system.

Naturally, the attribute system in Bizzkit PIM includes an attribute type that allows for referencing a specific brand. This feature enables users to connect products or other entities to their corresponding brands.

## Data binding

PIM offers two methods of data binding to ensure users select from a predefined list, which promotes consistency and accuracy in product data management. 

The first method, known as field level data binding, involves using a reference to a global or brand list in an attribute. This approach binds individual fields within an attribute to a centrally managed list. 

The second method, called value level data binding, is achieved by adding predefined values directly to an attribute. These predefined values act as a fixed set of options for users to choose from when managing product data. 

Both field level and value level data binding help maintain data integrity by guiding users to select from a list of approved values, rather than allowing free text input.

## Master and variant products

When creating a product in Bizzkit PIM, it only requires a few essential attributes, such as a unique name, and an optional External ID, which can be either text or a number. The External ID is not mandatory, so the unique name is the only required attribute. After this initial setup, it's up to the user to add any additional attributes that are relevant to the specific product. 

In PIM, a product that cannot be influenced by adding attributes or changing values of other products, is referred to as a single-level product and called a variant. This model is suitable for some businesses, particularly those with products that have significant differences and unique characteristics. 

Managing a large number of products with a single-level hierarchy can be challenging, especially when it comes to maintaining common attributes and values. In PIM, there are several methods to manage attributes across a range of products without having to edit each product individually. 

One approach is to use the bulk operations feature in PIM, which allows you to easily add or remove attributes and values for multiple products through the user interface. Another option for maintaining numerous products is by utilizing the import/export feature in PIM, which streamlines the process of updating product attributes and values in bulk.

Nevertheless, PIM simplifies maintenance by supporting an inheritance system where a product can serve as a master for other products. Any changes to attributes on the master product will automatically propagate to its variants (children). This is known as a multi-level product, and the hierarchy can be as wide and deep as necessary. A master product can also be a master for other master products, creating a chain of inheritance. In reality, businesses might typically have 2- or 3-level hierarchies, but the structure ultimately depends on the specific business model.

Of course, you have the flexibility to combine both single- and multi-level products when creating a PIM, ensuring that the system is as versatile and adaptable as possible to suit your unique needs. This combination allows you to leverage the strengths of both product types, making it easier to manage your product catalog and accommodate varying product relationships and attributes.

For instance, imagine a business selling merchandise. A dog collar with a printed business name might be modeled as a single-level product. Coffee mugs with printed names available in both ceramic and hard plastic might benefit from having a mug-master product with shared attributes, and the actual SKUs created as variants of the master. In the case of t-shirts, having a master product representing the generic t-shirt, followed by another master related to color, and then a range of variants representing sizes could be an effective model. This approach allows for a diverse product catalog with a mix of single- and multi-level products, tailored to the specific needs and relationships of the items being sold.

## Bundles

Another method of organizing products is by utilizing the built-in bundles feature. This feature allows you to create a product that acts as a container for a variety of combinations, including references to other products and their respective quantities. This approach enables the creation of product bundles or packages, streamlining the management of related items and providing customers with more purchasing options.

As previously mentioned, the attribute system includes an attribute type that allows you to reference other products in PIM, making it possible to easily model a bundle using a multi-field and multi-value attribute. However, by utilizing the built-in bundle feature, you gain the added advantage of being able to attach attributes to one or more of the bundled products. This capability can be particularly useful if you want to further describe the relationship between the products, such as providing a specific description used when the products are sold as part of the bundle. This added context enhances the product presentation and helps customers better understand the bundled offering.

## Product hierarchies

In PIM, products can be arranged into diverse product hierarchies, providing a structured organization for your catalog. These hierarchies can be as wide and deep as necessary, accommodating various levels of product categorization and relationships. A product can be associated with one or multiple nodes within a single hierarchy or across several hierarchies.

Moreover, each node within the hierarchy can be associated with one or more attributes, providing a highly flexible and customizable system for managing product information.

Hierarchies provide several advantages beyond just organizing products. For instance, you can add a so-called product enricher to a node. With a product enricher, you can ensure that products are automatically enriched with attributes and possibly values.

Another possibility within a hierarchy is to add a product validator that ensures a user cannot change a value that doesn't validate correctly. This feature helps maintain data integrity and accuracy, preventing users from accidentally inputting incorrect information or deviating from predefined standards.

## Customizable PLP in the UI

In PIM, there is an advanced Product Listing Page (PLP) that can be configured for each individual user. Users can control which attributes they want to be displayed, and the PLP also provides information about values across different segments. This personalized approach allows users to tailor their experience and access the most relevant product data for their needs.

Associated with the Product Listing Page (PLP) is the option for advanced filtering. Users have the ability to filter on various criteria, including free text, attributes and their values, master/variant hierarchies, and much more. These filters can be saved with a name and optionally which attributes are displayed on the PLP. This way, users can easily access a predefined collection of products tailored to their specific requirements or preferences, streamlining the product browsing process.

## Mass edit

When a user needs to modify multiple products, working with one product at a time can be time-consuming. Therefore, PIM offers a feature called Mass Edit, which allows users to edit products in a grid based on fields defined by a filter.

Mass Edit includes several functions for easy and quick modification of attribute values. This streamlines the process of updating product information across numerous items, saving time and ensuring consistency across the product catalog.

## Dashboards

Dashboards in PIM provide an efficient way to organize and manage collections of products, offering an excellent starting point for users to oversee the products they are responsible for. Dashboards can be personalized and tailored to individual user needs, and they can also be shared among team members to facilitate collaboration.

A variety of widget types can be added to a dashboard to create a comprehensive and customizable view of the product catalog. These widgets include:

- List: Showcase a collection of items or data points in a simple, easy-to-read format.
- Statistics: Display key metrics and data points.
- Donut chart: Visualize data in a circular chart format.
- Bar chart: Represent data using horizontal bars.

These widgets are based on data sets, which in turn are derived from filters. This allows users to create highly targeted and specific views of their product data, ensuring that they have access to the most relevant information for their needs.

## Bulk operations

In the Bulk Operations section of the Product Listing Page (PLP) within the user interface, users can access a powerful feature that allows them to perform a variety of actions on all products or a specific selection of products. 

These actions include:

- Place products in category
- Remove products from category
- Remove primary category
- Enrich products
- Add variant to master
- Remove variant from master
- Add to bundles
- Remove from bundles
- Update product
- Export products
- Unpublish products
- Delete products

Bulk operations offer a highly efficient way to manage product hierarchies, enrich and update product information, manage relationships between master products and their variants, handle product bundles, control product visibility, delete products, and export product data in a advanced and flexible CSV format. 

## Import

The import system in PIM allows users to seamlessly integrate data from external sources into the platform and automate several operations.

With the import system you can import the following:

- Products
- Brands
- Bundle items
- Global list items
- Predefined attribute values
- Product Hierarchies
- Attributes

The import system in PIM serves as a comprehensive solution for not only adding product data but also modifying and deleting it. This robust system allows users to efficiently manage their product information by integrating data from various sources and streamlining the process of maintaining product catalogs in PIM.

## Extensibility

PIM offers numerous expansion possibilities.

The API enables importing, exporting, modifying, and adding products, attributes, hierarchies, and more. This allows for the creation of automation code in a backend system to streamline processes.

Webhooks enable external systems to react to a range of events from PIM, such as the addition or modification of a product, through HTTPS requests. This facilitates real-time communication between PIM and other systems, promoting seamless integration and the automation of workflows.

The PIM user interface also offers numerous opportunities for expansion and customization. This flexibility allows you to tailor the system to better suit your specific needs and requirements, enhancing the overall user experience and optimizing the management of your product information. By extending the UI, you can incorporate new features, streamline workflows, and create a more efficient and user-friendly environment for managing your product catalog.

Custom bulk operations serve as an extension point in PIM, allowing you to execute custom operations or jobs on the product catalog that run on the customer's solution side. These operations are initiated in the same way as PIM's built-in bulk operations, enabling you to develop your own third-party integrations when your specific needs are not met by the existing operations.

Upon registering a new custom bulk operation, you must designate an endpoint on the customer solution that will be called when the operation is triggered from the UI. Additionally, you need to prepare the customer solution to receive and comprehend external bulk operation requests. When the endpoint is called, PIM specifies the system name of the operation being activated and the unique names of the products affected by the operation. Similar to built-in bulk operations, the set of impacted products is determined by the currently applied product filters or a user-specified selection of products.

UI Extension Frame Sets in PIM offer a powerful way to extend and customize the user interface to better accommodate your specific needs. By utilizing these frame sets, you can seamlessly integrate external URLs with parameters and display the resulting content either internally within PIM or externally in a separate window or tab. This provides an opportunity to incorporate additional features, enhance workflows, and create a more streamlined user experience when managing your product information.
