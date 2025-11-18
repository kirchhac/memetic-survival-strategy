# The Stars Within Us — Book Site

This repository contains the source for **The Stars Within Us**, a book about time, myth, and the cosmos, published using Mintlify.

The site is optimized for a chapter-based book structure, making it easy to add new chapters and update content.

## Book Structure

The book is organized as follows:

- **Introduction** (`book-introduction.mdx`) - The foundation of the book's thesis
- **Chapters** - Sequential chapters in the root directory:
  - `chapter-1-sky-as-teacher.mdx` - "Chapter 1: The Sky as the First Teacher"
  - `chapter-2-four-minute-drift.mdx` - "Chapter 2: The Four-Minute Drift"
  - `chapter-3-eleven-day-gap.mdx` - "Chapter 3: The Eleven-Day Gap"
  - `chapter-4-sexagesimal-universe.mdx` - "Chapter 4: The Sexagesimal Universe"
  - `chapter-5-sacred-numbers.mdx` - "Chapter 5: The Sacred Numbers"
  - *(and more chapters as they're added)*

All chapters are stored as `.mdx` files in the root directory and are automatically organized in the navigation via `docs.json`.

## Development

### Setup

Install the [Mintlify CLI](https://www.npmjs.com/package/mint) to preview your book locally:

```bash
npm i -g mint
```

### Local Preview

Run the following command at the root of your repository (where `docs.json` is located):

```bash
mint dev
```

View your local preview at `http://localhost:3000`.

## Adding or Updating Chapters

### Adding a New Chapter

1. **Create a new `.mdx` file** in the root directory with a descriptive filename:
   ```bash
   # Example: Chapter 6
   touch chapter-6-solar-hero.mdx
   ```

2. **Add frontmatter and content** to the file:
   ```mdx
   ---
   title: 'Chapter 6: The Solar Hero and the Lunar Trickster'
   description: 'How Sun, Moon, and stars became gods, demons, and heroes'
   ---
   
   # Chapter 6: The Solar Hero and the Lunar Trickster
   
   Your chapter content here...
   ```

3. **Add the chapter to `docs.json`** in the navigation section:
   ```json
   {
     "group": "Chapters",
     "pages": [
       "book-introduction",
       "chapter-1-sky-as-teacher",
       "chapter-2-four-minute-drift",
       "chapter-3-eleven-day-gap",
       "chapter-4-sexagesimal-universe",
       "chapter-5-sacred-numbers",
       "chapter-6-solar-hero"  // ← Add your new chapter here
     ]
   }
   ```

4. **Save and preview** - The site will automatically update in your local preview.

### Updating an Existing Chapter

1. **Edit the `.mdx` file** directly (e.g., `chapter-1-sky-as-teacher.mdx`)
2. **Save your changes**
3. **Preview locally** with `mint dev` to see your updates
4. **Commit and push** when ready to publish

### Chapter Naming Convention

For consistency, use this naming pattern:
- `chapter-{number}-{descriptive-slug}.mdx`
- Examples:
  - `chapter-1-sky-as-teacher.mdx`
  - `chapter-2-four-minute-drift.mdx`
  - `chapter-6-solar-hero.mdx`

The title in the frontmatter can be more descriptive (e.g., "Chapter 1: The Sky as the First Teacher"), while the filename should be a URL-friendly slug.

## Publishing Changes

### Automatic Deployment

1. **Commit your changes:**
   ```bash
   git add .
   git commit -m "Add Chapter 6: The Solar Hero"
   ```

2. **Push to your default branch:**
   ```bash
   git push
   ```

3. **Mintlify automatically deploys** - Changes are deployed to production automatically after pushing to the default branch (requires the [Mintlify GitHub app](https://dashboard.mintlify.com/settings/organization/github-app) to be installed).

### Manual Deployment

If you need to trigger a manual deployment, you can do so from the [Mintlify dashboard](https://dashboard.mintlify.com).

## File Organization

```
.
├── docs.json              # Site configuration and navigation
├── book-introduction.mdx  # Book introduction
├── chapter-*.mdx          # Individual chapter files
├── images/                # Images and assets
├── logo/                  # Logo files
└── README.md             # This file
```

**Note:** Original chapter markdown files are preserved in the `/book` folder for reference, but the published site uses the `.mdx` files in the root directory.

## Need Help?

### Troubleshooting

- **Dev environment isn't running:** Run `mint update` to ensure you have the most recent version of the CLI.
- **Page loads as 404:** Make sure you are running in a folder with a valid `docs.json` and that the page filename matches what's listed in `docs.json`.
- **Chapter not appearing:** Verify the filename in `docs.json` matches the actual `.mdx` filename (without the extension).

### Resources

- [Mintlify documentation](https://mintlify.com/docs)
- [Mintlify community](https://mintlify.com/community)
- [MDX documentation](https://mdxjs.com/) - For advanced formatting options
