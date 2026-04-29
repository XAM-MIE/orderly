# Orderly - UI Structure & Page Map

## Platform Overview

Orderly is a digital platform that connects university students to nearby restaurants and food vendors for fast ordering, payment, and delivery. It simplifies how people discover food, place orders, and receive deliveries through a seamless local network of vendors.

### Target Users
- University students ordering food on and around campus
- Food vendors/restaurants onboarding to sell to students

### Key Decisions
- **Campus Selection**: Auto-detect location with manual fallback selector in nav
- **Payments**: Credit/debit cards + bank transfers
- **Design System**: Based on Miro-inspired tokens (see DESIGN.md)

---

## Core User Flows

1. **Discover** -- browse vendors, search food, filter by cuisine/price/speed
2. **Order** -- customize items, add to cart, build a meal
3. **Pay** -- checkout with card or bank transfer, apply promos
4. **Track** -- real-time delivery status updates
5. **Account** -- profile, order history, saved addresses, payment methods

---

## Page Map

| Route | Page | Description |
|---|---|---|
| `/` | Homepage | Discovery engine -- hero, deals, popular vendors, trending items |
| `/explore` | Explore | Browse/search all vendors with filters, sort, and map view |
| `/vendor/[slug]` | Vendor Storefront | Vendor info, menu grouped by category, live cart sidebar |
| `/item/[id]` | Item Detail | Modal/drawer overlay for customizing a single item |
| `/cart` | Cart | Items added, quantity controls, subtotal, proceed to checkout |
| `/checkout` | Checkout | Delivery address, payment method, promo code, place order |
| `/order/[id]` | Order Tracking | Live status stepper, ETA, map, rider/vendor contact |
| `/account` | Account | Profile, saved addresses, payment methods |
| `/account/orders` | Order History | Past orders with reorder button |
| `/auth/login` | Login | Student login (university email) |
| `/auth/signup` | Sign Up | Create account with student details |

---

## Global Components

### Desktop Top Nav
- **Logo** (left) -- "orderly" wordmark in Near Black (`#1c1c1e`)
- **Search bar** (center-left) -- white bg input with `1px solid #e9eaef` border, 8px radius, placeholder in Input Placeholder (`#a5a8b5`)
- **Location pill** (center-right) -- auto-detected campus name with dropdown to switch
- **Cart icon** (right) -- with badge showing item count in Blue 450 (`#5b76fe`)
- **Avatar** (far right) -- initials circle, links to account

### Mobile Bottom Nav (5 tabs)
- **Home** -- homepage icon
- **Explore** -- search icon
- **Cart** -- shopping bag icon with count badge
- **Orders** -- delivery truck icon
- **Account** -- person icon

### Shared UI Components
- Vendor cards (image, name, rating, ETA, delivery fee, tags) -- 12px radius, ring shadow `rgb(224,226,232) 0px 0px 0px 1px`
- Food item cards (image, name, vendor, price, order count) -- 12px radius, white bg
- Category pill chips (emoji + label, scrollable) -- pastel backgrounds, 8px radius
- Cart sidebar/drawer (desktop: sticky sidebar, mobile: bottom sheet)
- Status badges (success, error, warning, info) -- pastel bg pairs from palette (e.g. coral light `#ffc6c6`, teal light `#c3faf5`, success `#00b473`)
- Form inputs (label above, helper text below, error states) -- white bg, `1px solid #e9eaef`, 8px radius, 16px padding
- Buttons: Blue 450 (`#5b76fe`) primary filled, outlined secondary (`1px solid #c7cad5`, 8px radius), ghost link

---

## Page Breakdowns

### 1. Homepage (`/`)

| Section | Description |
|---|---|
| Hero | White background. Left: eyebrow text in Roobert PRO Medium 14px, bold headline in Roobert PRO Medium 56px (-1.68px letter-spacing, line-height 1.15) ("Food from your campus, delivered fast."), subtext in Noto Sans 18px Slate (`#555a6a`), dual CTAs -- "Order Now" Blue 450 filled button, "Browse Vendors" outlined button (`1px solid #c7cad5`, 8px radius). Right: visual with floating stat cards on pastel backgrounds. |
| Quick Categories | Horizontal scrollable row of food category chips with emojis. All, Burgers, Pizza, Asian, Coffee, Healthy, African, Shakes, Pastries, Drinks, Late Night, Sides. Active state = Blue 450 filled chip. Inactive = outlined with border `#c7cad5`. |
| Deals Near You | Horizontal scroll of deal cards (12px radius, pastel bg pairs). Each: pastel gradient image, promo badge (e.g. "30% OFF", "FREE DELIVERY", "BOGO"), vendor name, deal description, countdown timer or condition text. |
| Popular on Campus | 3-column card grid of top-rated vendors. Each: food photo (12px top radius), vendor name in Roobert PRO Medium 24px (-0.72px), star rating, delivery time estimate, delivery fee, cuisine tags (Blue 450 outlined chips), promo/new badges. Card uses ring shadow `rgb(224,226,232) 0px 0px 0px 1px`. |
| Trending Now | 4-column grid of top-ordered dishes. Each: square photo (12px radius), dish name in Roobert PRO Medium 18px, vendor name in Noto Sans 16px Slate, price in Naira, "X ordered today" count. |
| New on Orderly | Horizontal scroll of recently onboarded vendors with "NEW" badge on teal light (`#c3faf5`) bg. Encourages exploration. |
| Campus Spots | 3-card grid (20px radius panels). Each: location photo, pastel overlay, spot name in Roobert PRO Medium 24px, vendor count and delivery estimate in Noto Sans 16px. |
| Vendor CTA Banner | Pastel coral light (`#ffc6c6`) section. Headline in Roobert PRO Medium 48px (-1.44px): "Run a food spot on campus? Join Orderly." Description in Noto Sans 18px, dual CTAs -- "Become a Vendor" Blue 450 filled, "Learn More" outlined. |
| Footer | 4-column layout on white bg. Brand description in Noto Sans 16px Slate. Company links, For Students links, For Vendors links. Bottom bar: copyright, Privacy Policy, Terms of Service, Cookie Settings. Divider using ring shadow border. |

### 2. Explore (`/explore`)

| Section | Description |
|---|---|
| Search Hero | Title in Roobert PRO Medium 48px (-1.44px) "Explore Vendors", large search input (white bg, `1px solid #e9eaef`, 8px radius, "What are you craving?" placeholder in `#a5a8b5`), category chip toolbar below. |
| Filters Sidebar (desktop) | Sort By dropdown, Price Range chips, Dietary checkboxes (Vegetarian, Vegan, Halal, Gluten-Free), Delivery Time ranges, Offers toggles (Free Delivery, Deals, New Only), Rating minimum. All inputs use 8px radius, `1px solid #e9eaef` borders. |
| Map Toggle | Button to toggle map view above results. Uses outlined button style. |
| Results Grid | 3-column vendor cards with ring shadow borders. Results count shown in Noto Sans 16px. "Load More" Blue 450 outlined button at bottom. |
| Mobile | Filters sidebar hidden. "Filters" button in toolbar opens filter sheet. Single-column results. |

### 3. Vendor Storefront (`/vendor/[slug]`)

| Section | Description |
|---|---|
| Header | Full-width hero image (20px radius), vendor name in Roobert PRO Medium 48px, star rating, review count, delivery time, delivery fee, cuisine tags (outlined chips), minimum order amount. |
| Info Bar | Operating hours, distance from user, "Info" and "Reviews" tab toggles -- active tab uses Blue 450 underline. |
| Sticky Menu Nav | Horizontal chips auto-scrolling to menu categories (Burgers, Sides, Drinks, Combos). Sticks below top nav on scroll. Active = Blue 450 filled, inactive = outlined. |
| Menu Sections | Grouped by category. Section title in Roobert PRO Medium 24px (-0.72px). Each item: thumbnail image (8px radius), name in Roobert PRO Medium 18px, short description in Noto Sans 16px Slate, price, "Add" Blue 450 button. |
| Cart Sidebar (Desktop) | Sticky right sidebar (20px radius, ring shadow border). Live cart: item list, quantity adjusters, subtotal, delivery fee, total in Roobert PRO Medium 24px, "Checkout" Blue 450 filled CTA. Empty state when no items. |
| Cart Drawer (Mobile) | Bottom sheet that slides up (20px top radius). Same content as sidebar. Floating cart button at bottom of screen shows item count and total on Blue 450 bg. |

### 4. Item Detail (`/item/[id]`)

Presented as a **modal/drawer overlay** (24px radius, white bg), not a full page.

| Element | Description |
|---|---|
| Image | Large item photo at top of modal (12px top radius). |
| Name & Description | Item name in Roobert PRO Medium 24px (-0.72px), description in Noto Sans 16px Slate below. |
| Customization Options | Size selector (Small/Medium/Large as chips -- active Blue 450, inactive outlined), extras/add-ons (checkboxes with prices), spice level (mild/medium/hot), special instructions textarea (white bg, `1px solid #e9eaef`, 8px radius). |
| Quantity Selector | Minus/plus buttons (outlined, 50% radius circles) with number display. |
| Add to Cart | Blue 450 filled button (8px radius, Roobert PRO Medium 17.5px 700 weight) showing total price. |

### 5. Cart (`/cart`)

| Element | Description |
|---|---|
| Vendor Header | Vendor name in Roobert PRO Medium 24px and link back to storefront. |
| Item List | Each: thumbnail (8px radius), name in Roobert PRO Medium 18px, customizations summary in Noto Sans 14px Slate, quantity adjuster (-, count, +), item total, remove button (X). Ring shadow card per item. |
| Order Note | Textarea (white bg, `1px solid #e9eaef`, 8px radius) for special instructions to the vendor. |
| Summary | Subtotal, delivery fee, service fee, promo discount (if applied), total. Total in Roobert PRO Medium 24px. Lines separated by divider border `#c7cad5`. |
| Promo Code | Input + "Apply" outlined button. Shows success (`#00b473`) or error (coral `#ffc6c6` bg) inline. |
| Checkout CTA | Full-width Blue 450 filled button "Proceed to Checkout" (8px radius, Roobert PRO Medium 17.5px). |

### 6. Checkout (`/checkout`)

| Section | Description |
|---|---|
| Delivery Address | Saved addresses as selectable cards (12px radius, ring shadow). Selected card gets Blue 450 ring highlight. "Add New Address" card with dashed border. Each shows label, full address, delivery instructions. |
| Delivery Instructions | Textarea (white bg, `1px solid #e9eaef`, 8px radius) for gate code, building, landmark. |
| Payment Method | Saved cards shown with last 4 digits (12px radius cards). "Add Card" option. "Bank Transfer" option showing account details. Card input form (number, expiry, CVV, cardholder name) -- all inputs 8px radius, `1px solid #e9eaef`. |
| Tip Selector | Chip options: No Tip, 100, 200, 500, Custom. Active = Blue 450 filled, inactive = outlined. |
| Order Summary | Collapsible recap of items, subtotal, fees, tip, promo, total. Dividers using `#c7cad5` border. |
| Place Order | Full-width Blue 450 filled CTA "Place Order -- total" (8px radius). Loading state during processing with spinner. |

### 7. Order Tracking (`/order/[id]`)

| Element | Description |
|---|---|
| Status Stepper | 4-step horizontal progress: Confirmed, Preparing, On the Way, Delivered. Active step highlighted in Blue 450 (`#5b76fe`). Completed steps use Success green (`#00b473`). Connector lines between steps. |
| ETA Display | Large countdown in Roobert PRO Medium 48px ("Arriving in ~12 min"). |
| Live Map | Rider location on map (placeholder for MVP). Vendor and delivery pin markers. Card overlay with 20px radius. |
| Contact Row | "Call Vendor" and "Call Rider" outlined buttons (8px radius, `1px solid #c7cad5`). |
| Order Summary | Collapsible section showing items ordered, quantities, prices. |
| Cancel Option | Small ghost link in coral dark (`#600000`) text to cancel (only available in early stages). |

### 8. Auth -- Login (`/auth/login`)

| Element | Description |
|---|---|
| Logo | Centered "orderly" wordmark in Near Black (`#1c1c1e`). |
| Form | Email input, password input (white bg, `1px solid #e9eaef`, 8px radius, 16px padding), "Forgot Password?" ghost link in Blue 450. |
| CTA | "Log In" Blue 450 filled button (full width, 8px radius, Roobert PRO Medium 17.5px). |
| Divider | "or" text with horizontal lines in `#c7cad5`. |
| Social | "Continue with Google" outlined button (`1px solid #c7cad5`, 8px radius). |
| Sign Up Link | "Don't have an account? Sign Up" in Noto Sans 14px, link in Blue 450. |

### 9. Auth -- Sign Up (`/auth/signup`)

| Element | Description |
|---|---|
| Form | Full name, university email, phone number, password, confirm password. All inputs: white bg, `1px solid #e9eaef`, 8px radius, 16px padding. |
| University Selector | Dropdown or search to pick university. Same input styling. |
| Terms | Checkbox: "I agree to Terms of Service and Privacy Policy". Links in Blue 450. |
| CTA | "Create Account" Blue 450 filled button (full width, 8px radius). |
| Login Link | "Already have an account? Log In" in Noto Sans 14px, link in Blue 450. |

### 10. Account (`/account`)

| Section | Description |
|---|---|
| Profile Header | Avatar (50% radius circle), name in Roobert PRO Medium 24px, email and phone in Noto Sans 16px Slate. "Edit Profile" outlined button. |
| Saved Addresses | Card list (12px radius, ring shadow) of delivery addresses. "Add Address" card with dashed border. |
| Payment Methods | Card list (12px radius) showing card brand, last 4, expiry. "Add Card" and "Add Bank Account" outlined buttons. |
| Favorites | Horizontal scroll of saved/favorite vendor cards (12px radius, ring shadow). |
| Settings | Notification preferences toggle, dark mode toggle, language selector. Toggle uses Blue 450 for active state. |
| Log Out | Ghost link in Slate (`#555a6a`) at bottom. |

### 11. Order History (`/account/orders`)

| Element | Description |
|---|---|
| Order Cards | Each (12px radius, ring shadow): vendor name in Roobert PRO Medium 18px, order date in Noto Sans 14px Slate, item count, total, status badge (Delivered = Success `#00b473` bg, Cancelled = coral light `#ffc6c6` bg). Thumbnail of first item. |
| Reorder Button | "Reorder" Blue 450 outlined button on each card -- adds same items to cart. |
| Order Detail Link | "View Details" ghost link in Blue 450 to order tracking page (shows completed state). |
| Tabs (optional) | "Active Orders" / "Past Orders" tab filter. Active tab = Blue 450 underline. |

---

## Mobile-First Notes

Students primarily use phones. All pages must be mobile-first:

- Bottom navigation bar (Home, Explore, Cart, Orders, Profile)
- Swipeable vendor cards in carousels
- Floating cart button on vendor pages (Blue 450 bg, shows count + total)
- Pull-to-refresh on tracking page
- Bottom sheet modals for item detail and filters (20px top radius)
- Full-width CTAs on mobile (no side-by-side layouts)
- Touch targets minimum 44x44px
- No hover-dependent interactions

---

## Responsive Breakpoints

| Breakpoint | Layout Changes |
|---|---|
| **Mobile** (<768px) | Single column, bottom nav, hamburger filters, stacked CTAs, bottom sheet modals |
| **Tablet** (768-1024px) | 2-column vendor grids, sidebar filters, compact nav |
| **Desktop** (1024-1440px) | 3-column grids, sticky cart sidebar, full filter sidebar, horizontal nav |
| **Large Desktop** (>1440px) | Max-width container (1440px) centered with auto margins |

---

## Design Tokens Reference

All colors, spacing, typography, shadows, and border radii are defined in `DESIGN.md` and implemented as CSS custom properties.

Quick reference:
- **Primary Interactive**: Blue 450 `#5b76fe`
- **Background**: White `#ffffff`
- **Heading text**: Near Black `#1c1c1e`
- **Body text**: Slate `#555a6a`
- **Borders/dividers**: Border `#c7cad5`
- **Input borders**: `#e9eaef`
- **Ring shadow**: `rgb(224,226,232) 0px 0px 0px 1px`
- **Success**: `#00b473`
- **Pastel accents**: Coral (`#ffc6c6`), Teal (`#c3faf5`), Rose (`#ffd8f4`), Orange (`#ffe6cd`), Pink (`#fde0f0`)
- **Display font**: Roobert PRO Medium (with OpenType variants)
- **Body font**: Noto Sans (with stylistic sets)
- **Cards**: 12px border radius, ring shadow elevation
- **Buttons**: 8px radius, Blue 450 filled or outlined with `#c7cad5` border
- **Spacing base**: 8px grid
- **Section padding**: 64-80px desktop, 48px mobile

---

## File Structure (Design System Mockups)

```
design-system/
  index.html          -- Design system component reference
  styles.css          -- All CSS tokens + component styles
  UI.md               -- This file
  homepage.html       -- Homepage mockup
  explore.html        -- Browse/search vendors mockup
  vendor.html         -- Vendor storefront + item modal mockup
  checkout.html       -- Cart + checkout + payment mockup
  tracking.html       -- Order tracking mockup
  auth.html           -- Login + signup mockup
  account.html        -- Profile + order history mockup
```
