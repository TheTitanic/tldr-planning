# TL~DR
## Resource Model
```
Account+-+Profile+-<Documents+-<Snippets+-<Translations+-<Comments
                              (created_by) (created_by)  (created_by)
                              ( profile  ) ( profile  )  ( profile  )
```

### Account
  * email
  * password_digest
  * **Relationships:**
    * has_one Profile

### Profile
  * Username
  * **Relationships:**
    * belongs_to Account
    * has_many Documents
    * has_many Snippets (created_by)
    * has_many Translations (created_by)
    * has_many Comments (created_by)

### Document
  * title
  * description
  * content
  * length
  * link to AWS, via Paperclip?
  * **Relationships:**
    * belongs_to Profile
    * has_many Snippets

### Snippets
  * content
  * start_position
  * end_position
  * **Relationships:**
    * belongs_to Document
    * has_many Translations
    * belongs_to Profile (created_by)

### Translations
  * heading
  * content
  * **Relationships:**
    * belongs_to Snippet
    * has_many Comments
    * belongs_to Profile (created_by)

### Comments
  * heading
  * content
  * **Relationships:**
    * belongs_to Translation
    * belongs_to Profile (created_by)
