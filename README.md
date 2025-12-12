# 12 Days of Christmas - Wordle Hints

A Wordle-style game for revealing Christmas gift hints! This project creates a fun, interactive way to give hints for presents by having the recipient play a Wordle game.

## How It Works

1. Create a comma-separated list of possible hints (5 letters each work best)
2. Base64 encode the list
3. Share a URL with the encoded hints as a parameter
4. The recipient plays Wordle to discover one randomly selected hint

## Usage

### Creating a Hint URL

1. List your hints separated by commas (e.g., "GIFT,TREE,BELLS,SNOWMAN")
2. Base64 encode the string
3. Add it to the URL with the `target` parameter
4. Optionally add the `id` parameter to number each day's present

### Example

For Day 1 hints: "GIFT,TREE,BELLS,SNOWMAN,BRACELET"

Encode to base64: `R0lGVCxUUkVFLEJFTExTLFNOT1dNQU4sQlJBQ0VMRVQ=`

Full URL: `https://yourusername.github.io/wordle-hints/?id=1&target=R0lGVCxUUkVFLEJFTExTLFNOT1dNQU4sQlJBQ0VMRVQ=`

This will display "Present #1" as the title.

### Encoding Base64

You can encode your hints using:

**Command Line (Linux/Mac):**
```bash
echo -n "GIFT,TREE,BELLS,SNOWMAN" | base64
```

**Online Tools:**
- https://www.base64encode.org/

**JavaScript Console:**
```javascript
btoa("GIFT,TREE,BELLS,SNOWMAN")
```

## Features

- Complete Wordle implementation with color-coded letter feedback
  - Green: Correct letter in correct position
  - Yellow: Correct letter in wrong position
  - Gray: Letter not in word
- On-screen keyboard and physical keyboard support
- Responsive design for mobile and desktop
- Randomly selects one hint from your list
- **Supports words from 4 to 8 letters long**
- **Confetti celebration when you guess correctly!**
- **Customizable title with Present # using the `id` parameter**
- Helpful subtitle: "Solve the wordle to get a hint about your present"
- **Progress tracking with localStorage** - solved hints are remembered
- **Smart hint selection** - unsolved hints are prioritized
- **Play Again button** - appears when hints remain unsolved

## Setting Up GitHub Pages

1. Push this repository to GitHub
2. Go to repository Settings
3. Navigate to Pages section
4. Under "Source", select "Deploy from a branch"
5. Select "main" branch and "/ (root)" folder
6. Click Save
7. Your site will be available at `https://yourusername.github.io/wordle-hints/`

## Tips

- **Words must be between 4-8 letters long**
- Mix different word lengths for variety
- Examples:
  - 4 letters: GIFT, TREE, STAR, BOOK
  - 5 letters: SCARF, WATCH, BOOTS, RINGS
  - 6 letters: CANDLE, TICKET, GLOVES
  - 7 letters: SWEATER, VOUCHER, PERFUME
  - 8 letters: NECKLACE, BRACELET, EARRINGS
- Mix easier and harder hints for variety throughout the 12 days
- You can mix different word lengths in the same encoded string
- Use the `id` parameter to create URLs for each of the 12 days (id=1 through id=12)

## Creating 12 Days of URLs

Example workflow:

```bash
# Day 1
echo -n "SCARF,GLOVE,BOOTS" | base64
# URL: ?id=1&target=U0NBUkYsR0xPVkUsQk9PVFM=

# Day 2
echo -n "WATCH,CLOCK,TIMER" | base64
# URL: ?id=2&target=V0FUQ0gsQ0xPQ0ssVElNRVI=

# ... and so on for all 12 days
```

## How Progress Tracking Works

- When a hint is correctly guessed, it's saved to localStorage
- Each URL (based on `id` and `target` parameters) has its own progress tracking
- On reload, the game prioritizes unsolved hints
- If unsolved hints remain, a "Play Again" button appears after winning
- Your wife can solve multiple hints from the same list until all are found!
- Progress is stored in the browser, so it persists across sessions
