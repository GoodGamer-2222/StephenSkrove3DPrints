# Project notes: local 3D-print shop website
Paste or upload this file at the start of a new chat so Claude can pick up where we left off.

## How we work (important)
- Claude is developer and design collaborator. **Claude proposes, the owner decides, then Claude implements.**
- For every decision or change except tiny ones: give options with pros and cons, recommend one, wait for the owner's choice, implement, then present the next decision.
- Prioritize: functional, simple for customers, easy to maintain, good-looking and trustworthy, expandable. Don't over-engineer.
- **File delivery rule:** if one file changed, give just that file. If two or more changed, give a zip of only the changed files.
- Always keep the real emails and alias below in `products.js` so the owner doesn't have to re-enter them.
- The owner sometimes edits `products.js` directly and may paste a newer copy. ALWAYS start from the owner's latest version, find their edits (diff it against the last version Claude sent), keep them, and apply new changes on top. Don't overwrite their wording.
- Keep this file updated after each decision.

## Setup
- Static site (HTML/CSS/JS, no framework) hosted on GitHub Pages. Orders go through FormSubmit.
- Files: `index.html`, `style.css`, `app.js` (logic, hash routing), `icons.js` (placeholder icons), `products.js` (shop info, categories, colors, products), plus `favicon.svg`, `favicon.png`, `apple-touch-icon.png`.
- In `products.js`: `email` = FormSubmit alias `3f9c325b5938415c6dbc39059dd14b69` (order requests go here); `contactEmail` = `stephenskrove@gmail.com` (shown to customers); `area` = Grants Pass.
- Shop name: "Stephen Skrove 3D Prints" (decided, option A). Chosen because Oregon generally doesn't require an assumed business name registration ($50, renewed every 2 years) when the name includes the owner's real name. Sources were inconsistent on how strict this is, so the owner should confirm with the Oregon Secretary of State and check local business license and income reporting rules. Not legal advice. Fallback if strict: name "Stephen Skrove" with "3D Prints" as a tagline. Owner's first name on the About page: Stephen. About text now says selling "in Grants Pass and beyond" since shipping was added.

## Business decisions
- Orders are requests only, no online payment. Pay at meetup by cash, Venmo, or Zelle. No tax or shipping handling.
- Fulfillment (form dropdown): meet up in person, local delivery ("there will be a small additional fee"), or ship it to me.
- Shipping (decided, ZIP-first option B): the form asks only for a ZIP code. The owner calculates shipping and emails the total, then asks for the full address if the customer goes ahead. Notice on the form and confirmation: shipping adds a small fee and the customer can cancel if it's too much. Payment for shipped orders is sent by email (`shipPayment` in `products.js`, currently Apple Pay or Zelle). The owner ships after payment. Assumed U.S. shipping only.
- Customers build a "request list" (cart), fill a form (name, email, optional phone, meetup/delivery, notes), and get a confirmation page with next steps.

## Products (replaced with the owner's full starting list: 23 items + 6 mystery boxes)
- 5 categories: Animals (12: gecko, chicken, wolf, cat, snake, Flexi Rex, slug, lizard, orca, spider, Flower Dragon, capybara), Vehicles (12), Desk Toys (thumb piano, thumb drum, fidget stick, Benchy), Functional (flat wallet, fish tank sign, fake egg), Mystery Boxes (6).
- Shop page has live search (product name, `tags`, category keywords; descriptions are not searched, so "car" doesn't return trucks; plural "cars" works) and category buttons. Home page shows only products with `featured: true` (Bobcat Tractor, Articulated Gecko, Flexi Chicken; the Bobcat replaced the Garbage Truck at the owner's request) plus a "See all products" button.
- Colors (owner's request): every non-mystery product offers all colors (Green, Gray, White, Yellow, Red, Blue, Purple) plus Silk Gold, Silk Red, the two glitter colors (Black / Blue Glitter, Black / Gold Glitter), and Colored (12 options), defined once as `ALL` in `products.js`. Exceptions: Fake Egg has no Colored (`NO_COLORED`); Fish Tank Sign has ONLY "Gray/Black and White". Mystery boxes have no color choice. Edit a product's `colors` or `soldOut` for a one-off change.
- Color option "Painted" was renamed "Colored" (white swatch with colored splashes). Meaning (owner): printed in white, then colored by hand to look realistic; method (paint or markers) undecided, so the site says "hand-colored". When a customer taps Colored on a product page, a note appears: "Colored means this one is hand-colored to look realistic." FAQ entry says exact coloring may vary slightly. Main color request (decided, option B): when Colored is tapped, an optional "Want a main color?" box (placeholder "e.g. pink") appears with "We'll confirm if we can match it." The request is saved per item (`want` in the request list), shown in the list, and included in the order email like "1 x Articulated Gecko (Colored, main color: pink)". Same item with different requests are separate lines. Also mentioned in the FAQ. Swatch is white with a few colored splashes. Fish Tank Sign has one option, "Gray/Black and White". Colors per product follow the owner's list.
- Eight animals were added later at $15 (snake), $8 (Flexi Rex), $5 (slug), $7 (lizard), $8 (orca), $5 (spider), $8 (Flower Dragon), $5 (capybara). Their colors (the 7-color set) and short descriptions are PLACEHOLDERS the owner should check. The lizard reuses the gecko icon.
- All descriptions were revised to be more descriptive about function and fun, not exact looks (photos will show that). Facts stay as the owner wrote them. Flower Dragon: articulated dragon whose sections look like lotus flowers or roses.
- Owner's own edits (kept): Flatbed Tow Truck is now "Flatbed Tow Truck With Car" at $15 (includes the small Skoda 120 car); Rocket Launcher Truck says "rugged truck"; Wolf description no longer mentions howling; Flexi Rex is "articulated" (not "partly"); extra search words on categories; "which adds to the fun" on five mystery boxes; FAQ wording about delivered orders and local meetup.
- Garbage Truck description now includes the author's details: working lever picks up a trash can and dumps its contents, working back door. Credit: WhopperPrinting.
- Garbage Truck REMOVED at the owner's request (the designer changed the file, so it can't be used). Its source line in the sources list is no longer relevant. Its icon remains unused in `icons.js`.
- Prices were updated using web research (Etsy flexi/dragon/snake listings, retail kalimba and toy truck prices). Now: Rocket Launcher Truck 13, Flatbed Tow Truck With Car 15, Cement Mixer 13, Backhoe 12, Tanker Semi 13, Container Semi 13, Off-road Semi 12, Long Dump Truck 12, Bobcat 8 (kept; research suggested 10), Simple Van 6, Simple Car 6, Gecko 10, Flexi Chicken 8, Snake 14, Flexi Rex 8, Slug 6, Lizard 8, Orca 8, Spider 6, Flower Dragon 13, Capybara 6, Wolf 6, Cat 5, Thumb Piano 8, Thumb Drum 9, Fidget Stick 3, Benchy 5, Flat Wallet 11, Fake Egg 4, Fish Tank Sign 5. Mystery boxes unchanged ($25 / $40). Open idea: a minimum order for shipping, since postage can exceed a $5 item.
- Open flag: the Benchy credit may name the wrong person (the original creators are reportedly Daniel Norée and Paulo Kiefe); owner hasn't decided to change it.
- Descriptions were lightly tidied. Facts were kept as the owner wrote them.
- Mystery boxes: a 4-item and an 8-item box for cars, articulated toys, and desk toys/functional items. No color choice (`mystery: true`); the request list shows "Surprise". Prices set by the owner: $25 for a 4-item box, $40 for an 8-item box.
- Placeholder pictures (owner chose option A): simple flat white icons (truck, semi, gecko, cat, etc.) drawn in code in `icons.js` on a favicon-style square tinted per category. Each product has an `icon` key in `products.js`. Real AI-generated images aren't possible for Claude here. Icons were not visually previewed by Claude (no renderer available), so the owner should check how they look and report any that look off. Replaced automatically when a product gets `images`.
- Removed with this change: Disk Shooter, Whistle, silk/glitter colors, and the Disk Shooter FAQ and small-parts notice (they weren't on the new list). Restore from the old `products.js` if wanted.
- Photos: see Photos section. Check that each design's license allows selling prints (still open).

## Design sources and licenses (all on Printables; checked by Claude's page fetch)
- Claude's page fetch never showed the License field (only a generic footer), so Claude did NOT verify licenses. The owner says they checked that each design is legal to sell before sending the links (second batch confirmed; first batch: owner to confirm Benchy, Flexi Chicken, Fake Egg, Thumb Drum, Tanker). Not legal advice.
- Credit lines ("Design by ... on Printables.") were added to the end of each product description so the credit is visible, not a tiny footer. Remove any that aren't wanted.
- Benchy Boat: https://www.printables.com/model/1098763-benchy-boat-3d (uploader Troy peterson, who marked it as his own original creation). The owner asked for credit to the linked uploader and says they can show his claim if challenged. Claude used neutral wording, "Model from Troy peterson on Printables.", instead of "Design by". Claude believes Benchy was originally made by Creative Tools (3dbenchy.com), so the uploader's claim may not protect the owner; consider using the official file and its license.
- Fidget Stick: https://www.printables.com/model/1188504-joystick-fidget-toy-free-to-sell (Leah Konapelsky / TinkerLink). Description says free to sell physical prints.
- Flexi Chicken: https://www.printables.com/model/920610-flexi-chicken-bslepicka-koko (Buchtomil). No sale statement seen.
- Cat Statue: https://www.printables.com/model/1380887-cute-cat-statue-free-to-sell (CHICKEMM / CLUCKWORKS3D). "Free to sell" in the title.
- Low Poly Wolf: https://www.printables.com/model/1701459-low-poly-wolf-free-to-sell (Sarathy Srinath). "Free to Sell"; listed size 50x60x100 mm (confirm it matches the owner's print).
- Articulated Gecko: https://www.printables.com/model/1423253-cute-gecko-articulated-toy-free-to-sell (Timmy). "Free to sell" in the title.
- Fake Egg: https://www.printables.com/model/792561-easter-egg-fun-for-kids/files (Ts3D). No sale statement seen. Owner prints only the realistic egg without the hole.
- Thumb Drum: https://www.printables.com/model/233091-thumb-drum (LoboCNC). No sale statement seen. Page says drumsticks clip into brackets and fulcrum pieces slide onto the levers (assembly).
- Tanker Semi: https://www.printables.com/model/255294-mini-truck-with-trailer-tanker-printed-in-one-piec (SHR3D.eu). No sale statement seen. Author warns of small parts, so a small-parts note was added to the product page. Same author likely made other vehicles on the site.
- Second batch, all by SHR3D.eu on Printables (credit line added to each description): Flatbed Tow Truck https://www.printables.com/model/385030-mini-car-tow-truck-printed-in-one-piece-without-su (folding ramp, rotating wheels, author warns of small parts, so a note was added); Container Semi https://www.printables.com/model/281170-small-truck-container-print-without-supports (owner prints only the plain container, not the pen-holder or crate-hole versions); Bobcat Tractor https://www.printables.com/model/236978-little-bobcat-printed-in-one-piece-without-support (author warns of small parts, note added); Rocket Launcher Truck https://www.printables.com/model/210683-small-truck-rm-70-vampire-4d-printed-in-one-piece (based on the RM-70 Vampire 4D); Off-road Semi https://www.printables.com/model/204992-small-truck-tatra-813-kolos-printed-in-one-piece (Tatra 813 KOLOS); Long Dump Truck https://www.printables.com/model/203724-small-truck-printed-in-one-piece; Cement Mixer https://www.printables.com/model/86386-little-beton-mixer-truck-maly-domichavac (the mix/barrel prints separately and is pushed into place).
- Third batch (credit lines added): Simple Car https://www.printables.com/model/85918-small-car-male-auticko and Simple Van https://www.printables.com/model/85917-small-van-mala-dodavka (both SHR3D.eu); Backhoe https://www.printables.com/model/233416-small-tractor-flexi-excavator-printed-in-one-piece (SHR3D.eu, "flexi excavator"); Flat Wallet https://www.printables.com/model/244198-fan-out-card-wallet (LoboCNC; each of 5 cards in its own pivoting sleeve); Garbage Truck https://www.printables.com/model/384417-functional-print-in-place-garbage-truck (WhopperPrinting; page says the lever picks up the trash can AND dumps its contents, plus a working back door, which our description doesn't mention; there are standard and mini versions that aren't simply scaled); Thumb Piano https://www.printables.com/model/443711-thumb-piano (Alpes86; 3 glued parts, author notes the sound is far from wood and metal ones); Fish Tank Sign https://www.printables.com/model/753128-fish-tank-and-aquarium-warning-sign (Daniel Oculus).
- Fourth batch (credit lines added): Flexi Rex https://www.printables.com/model/4035-flexi-rex (AgentSCAD; this is a REMIX of Kirbs's Flexi Rex on Thingiverse, so the original's license applies; credit names both); Articulated Snake https://www.printables.com/model/195000-articulated-snake (TechnicaL); Slug https://www.printables.com/model/229666-friendly-articulated-slugf (Copper Keep, who also sells prints of his designs at Copperkeep.com); Lizard https://www.printables.com/model/1537993-real-ones-from-a-real-author-flexi-gecko-articulat (Kris Cyber; page explicitly allows commercial use of prints and asks to be mentioned; says copycat uploads of his geckos exist, so the other gecko, by Timmy, is worth comparing); Orca https://www.printables.com/model/760041-articulated-orca (Mattes); Spider https://www.printables.com/model/899258-articulated-jumping-spider (Daann_ii; page allows selling printed models, not model files, and asks not to claim it as your own); Flower Dragon https://www.printables.com/model/907634-articulated-lotus-dragon (Daann_ii; same permissions); Capybara https://www.printables.com/model/1166421-articulated-pocket-pets-baby-capybara (Fulcrum Studio; page mentions "commercial licenses" on the author's Patreon, which suggests selling may need a separate license: owner must confirm).
- Owner says they checked each design's license before sending links. All designs are now sourced except none left.

## Design decisions made
- Color options: swatches that hint at the finish (silk sheen, glitter speckles), plus a per-product `soldOut` list. A note says colors vary slightly by spool. Later, real per-color photos for best sellers.
- Home page: option A. A one-line intro with the products right underneath, then the layer-line stripe and the how-it-works steps. Option C (a short "made by a local person" intro with a photo) is planned for later once the owner has a photo.
- Overall look: option A, keep the current look (calm frame so the colorful products stand out). Warmer accent than teal is an option if it ever feels too plain. Current look: cool off-white background, deep teal accent, print-layer-line stripe motif, Bricolage Grotesque font.

## Favicon
- The browser tab icon is the same layered-stripes mark as the header: `favicon.svg`, `favicon.png`, and `apple-touch-icon.png` (for iPhone home screen), linked in `index.html`.

## Photo uploader (decided: option A, built)
- `admin.html` (not linked from the shop) lets the owner pick a product, drop in photos, and upload straight to GitHub. It shrinks photos to 1200 px JPEGs, saves them in `images/` as `PRODUCTID-N.jpg`, and records them in `photos.js` (`PHOTOS[id] = { images: [...], defaultColor }`). `app.js` merges `photos.js` over `products.js`, so photos set there override `images` and `defaultColor` in `products.js`. Multiple photos at once (decided, option A): after choosing files, each photo gets its own thumbnail row with a product dropdown (default = the product chosen above, changeable per photo, × removes it from the upload). Uploads run one after another; on any error the page saves what succeeded and reloads the real list from GitHub; a taken file name is retried with the next number. The page also supports Make main, Remove (removes from the list only; the file stays in the repo), and a default color per product.
- It uses a GitHub fine-grained personal access token (repo access: only StephenSkrove3DPrints; permission: Contents read and write) pasted once and kept in the browser on that device. The token is the real lock; a page-side passcode can't protect a static site. Never share or commit the token. Revoke it on GitHub if lost. Repo: goodgamer-2222/StephenSkrove3DPrints. Branch is auto-detected as the repo's default branch.
- Not tested against GitHub by Claude (no network access here). The owner's first real upload is the test. New photos take a minute or two to appear after GitHub rebuilds the site.
- Files: `admin.html`, `photos.js` (new), `index.html` and `app.js` (updated to load photos.js).

## Price/stock editor and announcement bar (decided, built)
- `admin.html` now has three tabs: Photos, Prices & stock, Announcement. Prices & stock: edit any price, tick "Home" for home page products, mark sold-out colors per product, and mark colors out of stock everywhere. Announcement: turn a one-line top bar on/off and edit its text.
- Saved in `settings.js` (`SETTINGS = { products: { id: { price, soldOut, featured } }, soldOutColors: [], announcement: { on, text } }`), which `app.js` merges over `products.js` (like `photos.js`). Only differences from `products.js` are stored. Cart items are re-priced to current prices on load, and items for removed products are dropped.
- New files: `settings.js`; `index.html` loads it and has the `#announce` bar; `style.css` styles it. Don't re-upload an empty `settings.js` from a zip after using the admin page, or settings will be erased.

## Custom Print page and Care page (decided, built)
- `#/custom`: explains what can be asked for (color combos or a main color, a design found online with a link, bigger batches), what may be refused (copyrighted/branded items, weapons, too big or delicate; DRAFT wording the owner hasn't approved), and a price note (quote after seeing the request, nothing charged until agreed). Short form (name, email, phone optional, what to make, design link, size, colors, quantity, needed by, meetup/delivery/ship) sent through FormSubmit like orders; success shows `#/customsent`. Chosen: option C.
- `#/care`: looking after prints (PLA heat warning, damp cloth, not food-safe, gentle with joints, small parts; general PLA knowledge, owner should confirm) and how to use the Thumb Drum, Thumb Piano, and Flat Wallet. Content lives in `CARE` in `products.js`. Products with a CARE item show a "How to use it" link to their section.
- Thumb Drum video: the owner's 6.1 MB file goes in the repo as `videos/thumb-drum.mp4` (MP4 plays everywhere; iPhone MOV may not). Thumb Piano and Wallet videos come later: set their `video` path in `CARE`. If a video file is missing, the page says "Video coming soon."
- Links (decided, option B): footer links "Custom prints" and "Care & how-to"; the shop page custom note and the no-search-results message link to the custom page; FAQ custom answer points to the footer link. Not in the top menu.

## Editing more from admin.html (A and B decided and built; D pending)
- Wording tab: edit a product's name, description, and designer credit. Credits were split out of descriptions into a separate `credit` field. On the shop the credit now reads as part of the same paragraph as the description (owner's request), not a tiny footer or a separate line. Clearing a credit asks for confirmation.
- Shop & pages tab: meetup spots, reply time, meetup payment wording, shipped-order payment options, area; the FAQ (add/remove/edit; placeholders {contactEmail}, {payment}, {shipPayment}, {area} fill in automatically); the Care page tips and each how-to text and video path.
- Email addresses (`email` FormSubmit alias and `contactEmail`) are NOT editable from admin, and `app.js` only accepts overrides for the five shop fields above even if `settings.js` is tampered with.
- Stored in `settings.js` (`shop`, `faq`, `care`, and per-product `name`/`desc`/`credit`), merged over `products.js` by `app.js`.
- D built (Add & remove tab): add a product with name, price, category dropdown (mystery category = no colors), color checkboxes (the standard 12 + Colored pre-ticked), description, credit box, and optional photos (no icon; products without a photo show a colored square with initials). Added products live in `settings.added`; their photos go in `photos.js` like any product. Hide/Show works for every product (`settings.products[id].hidden`, removed from the shop but kept so it can return); Delete (with confirmation) works only for products added in admin. Original `products.js` products can be hidden, but deleting them needs a file edit by Claude.

## Labels (NEW, BEST SELLER, etc.)
- Each product can have one short label (up to 20 characters, free text with suggestions NEW, BEST SELLER, LIMITED, BACK IN STOCK, SALE). Set it in admin: Wording tab (any product) or the Add & remove form (new products), or `label: "NEW"` in `products.js`. Shown as a pill badge on the photo corner of product cards and above the title on the product page. Searching for the label text finds those products.

## Form sending check (fix)
- Owner reported order and custom print requests not working. Claude can't test FormSubmit from here. Found that the forms only checked the HTTP status, but FormSubmit can reply OK with `success: "false"` (for example when the alias needs activation), which would show the thank-you page without sending any email. Both forms now read FormSubmit's reply, stay on the form on failure, and show FormSubmit's message in the error line. Both forms also now show an "Or click here to email this request to us" link on failure (a prefilled mailto), so no request is lost. FormSubmit docs found by search: each recipient/form combination may need activation (confirm any activation email), the first submission is held until activation, and autoresponses are NOT supported for AJAX submissions or when its captcha is off (which is why the old auto-reply never worked). Next step is the owner's report of what message appears, and checking the inbox/spam for a FormSubmit activation email.

## Size, weight, and included (decided: option C, built)
- Per product: a parts list (name, weight in grams, length/width/height in mm) and an "included" line, e.g. Flatbed Tow Truck With Car: tow truck + Skoda 120 car parts, "1 tow truck and 1 Skoda 120 car". Entered in admin's Size & weight tab (stored in `settings.js` as `parts` and `included`, or `parts`/`included` in `products.js`). The product page shows an "Included" line and a parts table with sizes in mm and inches. Weights are PRIVATE by default: the order email gets `total_weight` (parts summed times quantity, flagged if some items have no weight). A shop-wide admin switch (`showWeights`) shows weights, per-part and total, in grams and ounces. No sample numbers were entered; the owner fills them in.

## Photos (decided)
- Mix of approaches: print the first item of each kind, photograph it on the print bed with the owner's light, plus an in-hand shot for scale and an in-use shot.
- Color rule (option C): main photo and in-hand photo use the same mid-tone color (blue or red work well; avoid black and white). The in-use photo can be any color.
- Gallery is built: `images: [...]` in `products.js`, first photo is the main one (also used on cards), thumbnails switch the main photo. `defaultColor` preselects the color matching the main photo.
- (Manual way, now replaced by the uploader) How to add photos: make an `images/` folder in the repo, use short lowercase names with no spaces (e.g. `benchy-1.jpg`), resize to about 1200 px wide (under ~500 KB each), roughly square with the subject centered (the site crops to a square), list them in `images` (print-bed shot first), set `defaultColor`, push to GitHub.

## Order form (decided: option B)
- Customer picks meetup or local delivery. Meetup shows a dropdown of public spots from `SHOP.meetupSpots` in `products.js` (plus "work out a spot by email"). Delivery shows an address box instead. Both ask for days/times that work, plus optional notes.
- `meetupSpots` currently has one spot: "Dutch Bros Coffee, 332 NW 6th St". More can be added.
- The refund/replace line was removed from the confirmation page (owner tells customers after payment and shipping). It's still in the About page FAQ. Reply time on the confirmation page is now "within a day or two".
- Bug fixed: the form select's id `ful` shadowed the function of the same name inside the form's inline handler, so the show/hide logic never ran. Function renamed `showFul`. Lesson: avoid function names that match form element ids or names.
- The confirmation page previously claimed a copy was emailed to the customer. That was wrong (FormSubmit doesn't do that by default), so the sentence was removed.

## Customer replies (decided: option A)
- The FormSubmit auto-reply never worked and was removed. The owner replies personally to each request (FormSubmit sets the customer as reply-to, so just hit Reply).
- The confirmation page says who the reply comes from (`contactEmail`) and how soon (`replyTime` in `products.js`), and to check spam.
- Reply template: "Hi [name], thanks for your order! [qty x item (color): available / ready by date / sold out, alternatives]. Total: $__, paid by cash, Venmo, or Zelle at pickup. Meetup: [spot] on [day] at [time]. Does that work? Let me know and I'll get printing."

## Custom orders (decided: option B)
- No form. A note on the shop page and a "Custom prints" footer link open an email to `contactEmail` with the subject "Custom print request". Owner decides each request case by case.

## Availability and lead time (decided: option A, for now)
- The site says nothing about lead time. The owner answers it in the personal reply. When bigger, longer-printing items are added, revisit with option C (a lead time per product, e.g. a `leadTime` field shown on the product page).

## Website address (decided: option A)
- Use the free GitHub Pages address. The site is partly just for fun. A custom domain can be added later.

## About and FAQ page (decided and built)
- New `#/about` page, linked in the header: short story, FAQ list (editable `FAQ` array in `products.js`), and a "Browse the shop" button. Owner name shown (`ownerName` in `products.js`, currently blank until the owner supplies it); photo later via `ownerPhoto`.
- Story text (Claude's edit of the owner's rough wording): got a printer, enjoys it, sometimes a print fails and that's annoying, now selling favorites locally.
- Visual polish pass (hover effects, tidier header/intro, nicer illustrations) is planned for after real photos exist.

## Problem prints (decided: option B)
- If a customer sends a photo of a problem, the owner will happily refund or replace. Stated in the About page FAQ and on the confirmation page.

## Visual polish (decided: option A, done)
- Header has a layer-stripe mark next to the shop name and a bottom border. Nav links underline on hover. The request list count is a badge. Product cards lift on hover. Buttons have press feedback. Respects reduced-motion. Colors and layout unchanged.
- Bigger visual gain still waits on real product photos.

## Link previews (decided: text now, image later)
- Title, description, and Open Graph tags are in `index.html` (name and description hardcoded there, so update them if the shop name or area changes).
- Later: add `og:image` (needs the final site address and a good image or product photo).

## Launch (decided: soft launch first, option A)
- Share the link with a few friends or family first. Ask them to place a real order request from their phone, then reply to each personally and set up a meetup.
- Ask them: Was it clear what to do? Did anything confuse you? Did the form and confirmation work? Anything look off on your phone?
- Check that requests arrive (and not in spam), and that colors, prices, and meetup spots look right.
- After feedback, decide on a public launch (local groups) and whether to wait for photos first.

- Videos on product pages: owner chose to skip for now (options were short clips in the repo, YouTube links, or photos only).

## Next decision
- Open items: and feedback on how the icons look.

## To do
- [ ] Push latest files to GitHub, test on a phone
- [ ] Confirm the name/registration question with the Oregon Secretary of State
- [ ] Consider adding more public meetup spots to `meetupSpots` in `products.js`
- [ ] Take and add real product photos
- [ ] Owner to check descriptions, add sizes, confirm prices
- [ ] Add own photo (`ownerPhoto`) for the About page
- [ ] Add `og:image` link preview picture once photos and site address are final
- [ ] Later ideas: payment links, shipping options, size options, per-color photos
