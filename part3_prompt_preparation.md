## Part 3: Prompt Preparation

**Selected PR:** PR #3145 – Playlist plugin  
**Link:** https://github.com/beetbox/beets/pull/3145

---

### 3.1.1 Repository Context

The beets repository is a music library management system that helps users organize and manage their music collections. It works like a digital librarian that keeps track of music files and makes it easy to find and enjoy songs and albums.

The intended users of beets are music enthusiasts who want their music collections to stay organized and easy to access. These users usually care about accurate music information and a clean library structure.

Beets focuses on solving problems related to music library management. It allows users to store, manage, and retrieve music metadata such as song titles, artist names, album details, and release dates. By using beets, music collections become searchable and easier to maintain.

In simple terms, beets helps music lovers take control of their music libraries. It is flexible and user-friendly, making it suitable for anyone who wants a better way to manage their music.

Overall, beets provides a more organized and enjoyable music experience by helping users quickly find and understand their music.

---

### 3.1.2 Pull Request Description

PR #3145 introduces an important improvement to beets by adding support for storing the original release year of songs and albums.

Before this change, beets stored only one release year. This caused confusion when music was re-released. For example, a song originally released in 1980 but re-released in 2000 would only show the 2000 date. This made it difficult to know the true original release year.

This pull request adds a new field called `original_year`. This field stores the year when the music was first released. Users can now see both the original release year and the release year of their specific version.

This change helps users better understand the history of their music and makes beets a more accurate and useful music library management tool.

---

### 3.1.3 Acceptance Criteria

- When a user imports a new album, the system should show a field called `original_year` where the original release year can be entered.
- When a user views the music library, the system should display the `original_year` value for each album.
- When a user edits the original release year, the system should save the updated value correctly.
- The system should handle missing original release years by leaving the field empty without showing errors.
- When an album has been re-released, the system should keep the original year and re-release year separate.

---

### 3.1.4 Edge Cases

1. **Missing original year information**  
   The system should allow the `original_year` field to remain empty without causing errors or showing incorrect data.

2. **Same album name with different original years**  
   The system should keep album data separate and avoid mixing information between different releases.

3. **Unrealistic year values**  
   If very old or future years are entered, the system should validate the input and warn the user.

---

### 3.1.5 Initial Prompt

You are working with the **beetbox/beets** repository. This project is a music library management system that helps users organize and manage their music collections. It stores information about songs and albums, including artist names, album titles, and release dates. The system also supports plugins and command-line tools to extend functionality.

Currently, beets stores only one release year for each album. This creates a problem for music that has been released multiple times. Users often want to know when an album or song was first released, not just when their copy was issued.

The task is to add a new metadata field called `original_year`. This field should store the original release year of a song or album. The goal is to allow users to keep both the original release year and the release year of their specific version.

#### Requirements

1. Add a new field called `original_year` to the album metadata in the database schema.
2. Update the library code to store and retrieve the `original_year` field correctly.
3. Modify the user interface so users can view and edit the `original_year` field.
4. Make the `original_year` field optional.
5. Ensure the new field works alongside the existing release year field.
6. Maintain backward compatibility so existing music data continues to work.

#### Acceptance Criteria

- When importing an album, users should be able to add an original release year.
- When viewing the library, the original release year should be visible.
- Editing the original release year should save changes correctly.
- Missing original release years should not cause errors.
- Original release year and re-release year should remain separate.
- Existing albums should remain unchanged and safe.

#### Edge Cases

1. Missing original year information  
   The system should allow empty values without errors.

2. Same album name with different original years  
   Album data should remain separate and accurate.

3. Invalid year values  
   The system should warn users when unrealistic years are entered.

#### Testing Requirements

After implementation, verify the following:
- Import an album and add an original release year.
- View the album and confirm the original year displays correctly.
- Edit the original year and confirm changes are saved.
- Import albums without an original year and check for errors.
- Verify older albums still work without data loss.
- Run existing tests to ensure no regressions occur.
