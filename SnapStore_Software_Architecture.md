# Business Rules

## User Authentication:

- Users must register and log in to access the SnapStore application.
- Authentication is required to perform actions such as making purchases, managing the cart, creating albums, uploading photos, creating projects, and viewing purchase history.

## Purchase Rules:

- Only authenticated users can make purchases (photos, albums, or projects).
- Users can view their purchase history.

## Cart Rules:

- Users can add items (photos, albums, or projects) to their cart.
- Authentication is required to add items to the cart.
- Users can view and modify the contents of their cart.
- Users can remove items from the cart.

## Album Rules:

- Users can create albums to organize their photos.
- Albums should have a title and an optional description.
- Only authenticated users can create albums.
- Albums can be set as public or private (private albums are only visible to the user).

## Photo Rules:

- Users can upload photos to the platform.
- Photos should have a title, description, image file, and price.
- Only authenticated users can upload photos.
- Users can assign photos to categories and add hashtags.
- Only the user who uploaded a photo can delete or update its details.

## Project Rules:

- Users can create photography projects.
- Projects should have a title, description, start date, and end date.
- Only authenticated users can create projects.
- Users can assign photos to projects they create.
- Only the user who created a project can delete or update its details.

# Protected Routes (Authenticated Users Only)

## User Profile:

- Access: /profile
- Description: Authenticated users can view and update their profile information.

## Cart Operations:

- Access: /cart
- Description: Authenticated users can view, add, update, and remove items in their cart.

## Purchase History:

- Access: /purchases
- Description: Authenticated users can view their purchase history.

<!-- ## Album CRUD:

- Create: /albums/create
- Read: /albums/:albumId
- Update: /albums/:albumId/edit
- Delete: /albums/:albumId/delete -->

## Photo CRUD:

- Create: /photos/create
- Read: /photos/:photoId
- Update: /photos/:photoId/edit
- Delete: /photos/:photoId/delete

<!-- ## Project CRUD:

- Create: /projects/create
- Read: /projects/:projectId
- Update: /projects/:projectId/edit
- Delete: /projects/:projectId/delete -->

# Publicly Accessible Routes (No Authentication Required)

## Home Page:

- Access: /
- Description: Publicly accessible homepage with featured content.

## Browse Photos:

- Access: /photos
- Description: Publicly accessible page to browse and search for photos.
<!-- 
## Browse Albums:

- Access: /albums
- Description: Publicly accessible page to browse and search for albums.

## Browse Projects:

- Access: /projects
- Description: Publicly accessible page to browse and search for projects.

## View Public Album:

- Access: /albums/:albumId
- Description: Publicly accessible page to view a public album and its contents. -->

## View Public Photo:

- Access: /photos/:photoId
- Description: Publicly accessible page to view details of a public photo.

# ERD

**User:**

- Represents registered users of the SnapStore.
- Attributes:
  - user_id (Primary Key)
  - username
  - email
  - password_hash
  - role
- Relationships:
  - One-to-Many with PhotoPurchase: One user can purchase multiple photos.
  - One-to-Many with AlbumPurchase: One user can purchase multiple albums.
  - One-to-Many with ProjectPurchase: One user can purchase multiple projects.
  - One-to-Many with Cart: One user can have multiple items in the cart.

**Photo:**

- Represents individual photos uploaded by users.
- Attributes:
  - photo_id (Primary Key)
  - title
  - description
  - image_url
  - upload_date
  - price
- Relationships:
  - Many-to-One with User: Many photos can belong to one user.
  - Many-to-Many with Category: A photo can belong to multiple categories.
  - Many-to-Many with Hashtag: A photo can have multiple hashtags.
  - Many-to-Many with PhotoPurchase: A photo can be purchased by multiple users.

<!-- **Project:**

- Represents photography projects created by users.
- Attributes:
  - project_id (Primary Key)
  - title
  - description
  - start_date
  - end_date
  - price
- Relationships:
  - Many-to-One with User: Many projects can belong to one user.
  - Many-to-Many with Category: A project can belong to multiple categories.
  - Many-to-Many with Hashtag: A project can have multiple hashtags.
  - Many-to-Many with ProjectPurchase: A project can be purchased by multiple users.

**Album:**

- Represents user-created albums containing photos.
- Attributes:
  - album_id (Primary Key)
  - title
  - description
  - creation_date
  - price
- Relationships:
  - Many-to-One with User: Many albums can belong to one user.
  - Many-to-Many with Photo: An album can contain multiple photos.
  - Many-to-Many with AlbumPurchase: An album can be purchased by multiple users. -->

**Transaction:**

- Represents user transactions, including purchases.
- Attributes:
  - transaction_id (Primary Key)
  - user_id (Foreign Key)
  - transaction_date
  - amount
- Relationships:
  - Many-to-One with User: Many transactions can belong to one user.
  - Many-to-Many with PhotoPurchase: A transaction can include multiple photo purchases.
  - Many-to-Many with ProjectPurchase: A transaction can include multiple project purchases.
  - Many-to-Many with AlbumPurchase: A transaction can include multiple album purchases.

**Category:**

- Represents categories to which photos and projects can be assigned.
- Attributes:
  - category_id (Primary Key)
  - name
- Relationships:
  - Many-to-Many with Photo: A category can have multiple photos.
  - Many-to-Many with Project: A category can have multiple projects.

<!-- **Hashtag:**

- Represents hashtags associated with photos and projects.
- Attributes:
  - hashtag_id (Primary Key)
  - name
- Relationships:
  - Many-to-Many with Photo: A hashtag can be associated with multiple photos.
  - Many-to-Many with Project: A hashtag can be associated with multiple projects. -->

**PhotoPurchase:**

- Represents the purchase of individual photos by users.
- Attributes:
  - photo_purchase_id (Primary Key)
  - user_id (Foreign Key)
  - photo_id (Foreign Key)
- Relationships:
  - Many-to-One with User: Many photo purchases can belong to one user.
  - Many-to-One with Photo: Many photo purchases can include one photo.
  - Many-to-One with Transaction: Many photo purchases can be part of one transaction.

<!-- **AlbumPurchase:**

- Represents the purchase of user-created albums by users.
- Attributes:
  - album_purchase_id (Primary Key)
  - user_id (Foreign Key)
  - album_id (Foreign Key)
- Relationships:
  - Many-to-One with User: Many album purchases can belong to one user.
  - Many-to-One with Album: Many album purchases can include one album.
  - Many-to-One with Transaction: Many album purchases can be part of one transaction. -->

<!-- **ProjectPurchase:**

- Represents the purchase of photography projects by users.
- Attributes:
  - project_purchase_id (Primary Key)
  - user_id (Foreign Key)
  - project_id (Foreign Key)
- Relationships:
  - Many-to-One with User: Many project purchases can belong to one user.
  - Many-to-One with Project: Many project purchases can include one project.
  - Many-to-One with Transaction: Many project purchases can be part of one transaction. -->

**Cart:**

- Represents a user's shopping cart.
- Attributes:
  - cart_id (Primary Key): Uniquely identifies each cart item.
  - user_id (Foreign Key): Links the cart item to a specific user, allowing for a many-to-one relationship.
  - item_id (Foreign Key): Used to reference the purchased item (e.g., a photo, album, or project). Ensure that this foreign key is correctly linked to the respective item tables (e.g., Photo, Album, Project).
  - item_type (e.g., "photo," "album," "project"): Used to differentiate between types of items in the cart.
- Relationships:
  - Many-to-One with User: A cart item belongs to one user. This relationship associates cart items with specific users.
  - Many-to-One with Photo: If item_type is "photo," establish a many-to-one relationship with the Photo model. This links the cart item to a specific photo.
  <!-- - Many-to-One with Album: If item_type is "album," establish a many-to-one relationship with the Album model. This links the cart item to a specific albAum.
  - Many-to-One with Project: If item_type is "project," establish a many-to-one relationship with the Project model. This links the cart item to a specific project. -->
