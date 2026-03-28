- X Clone - exTwitter
 I have built a complete front-end clone of X (formerly Twitter), replicating pretty much everything you would expect from the real platform. Every piece of the interface is there—the left navigation sidebar with all its interactive menu items, the central feed where posts show up, and the right sidebar with search, trending topics, and suggested accounts to follow.

How the Layout Works
I followed X's signature three-column layout, building everything with Bootstrap 5's grid system. The layout handles responsive behavior smoothly, adjusting spacing and visibility based on screen size without needing custom code for every breakpoint.

Desktop Layout
The left column holds the main navigation menu with icons and text labels, and it stays fixed while scrolling—exactly like X's sidebar. The middle column contains the main feed area with a sticky top navigation bar showing "For you," "Following," and "Communities" tabs, plus the tweet composer and the scrolling feed of posts. The right column shows supplementary content: a search bar, a "Subscribe to Premium" promotional card, trending topics in the "What's happening" section, suggested accounts to follow, and footer links.

Bootstrap's responsive grid system makes sure this layout adapts across devices. On tablets, the right column disappears to give more room to the main feed. On mobile, both side columns are hidden entirely, replaced by a bottom navigation bar and a menu panel that users can access by swiping.

Custom CSS Work
 I wrote custom CSS for the X-specific styling and downloaded svg's for compinents that Bootstrap doesn't cover. Sticky positioning keeps the sidebars fixed during scrolling. Hover effects on navigation items and post cards provide visual feedback when users interact with them. Modal animations make the post detail view, settings panel, and mobile menu feel smooth when they open and close.

 

The complete light and dark theme system relies on custom CSS classes that override Bootstrap's default colors. I also wrote mobile-specific styles to control the bottom navigation bar and swipe panel that appear only on smaller screens.



JavaScript Functionality
I built all the dynamic behavior with vanilla JavaScript. No frameworks, no libraries—everything from data management to DOM manipulation uses native browser APIs.



Post Data Management
All posts are stored in a JavaScript array. Each post object contains metadata: the user's name and handle, profile image path, verification status, timestamp, post content, media type and URL, and counters for comments, retweets, likes, and polls. This data structure lets the application post , render and update posts in real time without static html posts.



Dynamic Feed Rendering
When the page loads, a function loops through the posts array and generates HTML for each post on the fly. This approach enables real-time updates—new posts appear instantly at the top of the feed without refreshing the page. Filtering between "For you," "Following," and "Communities" views simply applies different filters to the same data array and re-renders the feed. Search functionality works the same way, filtering posts by content, username, or handle as the user types.



Interactive Post Actions
Like Button: When a user clicks the heart icon, the application checks whether the post is currently liked. If unliked, the outlined heart becomes filled, turns red, and the like counter goes up. If liked, it switches back to an outlined heart and the counter goes down. The post's like count in the data array updates at the same time, keeping everything consistent across all views.



Retweet Button: Clicking the retweet icon toggles a green color state and updates the retweet counter. A custom CSS class tracks the retweeted state, letting the application accurately increment or decrement the count based on the user's action.



Comment System: Clicking the comment icon reveals a hidden reply section with a textarea and submit button. When a user submits a reply, a new comment appears in the comments container, the comment count updates, and the post's comments property increments in the data array. Comments remain visible for the current session and contribute to the post's engagement metrics.



Share Button: Clicking the share icon copies the post content to the system clipboard. A temporary notification pops up at the bottom of the screen to confirm the action.



Modal Systems
Post Detail Modal: When a user clicks anywhere on a post except interactive elements like buttons, images, or videos, a modal opens showing the full post with expanded content, media, and interaction buttons. This modal stays in sync with the main feed—likes, retweets, and new comments update both the modal view and the underlying post data. The modal includes a reply section and displays existing comments with their own like functionality.



Settings Modal: The settings panel uses a two-column layout. The left column contains navigation tabs for Display, Notifications, Privacy, Accessibility, and Data usage. The right column dynamically renders content based on which tab is selected. The Display tab includes a theme toggle between Dark and Light modes and a font size slider. The Notifications tab provides toggle switches for push and email notifications. The other tabs serve as placeholders for future functionality.



More Options Modal: Clicking the "More" button in the left sidebar opens a dropdown card positioned below the button. This card contains eight options: Lists, Communities, Bookmarks, Creator Studio, Business, Ads, Create your space, and Settings and privacy. Each option currently shows a "Coming soon" notification, with the Settings option opening the full settings modal.



Theme System
The application supports both Dark and Light modes with full persistence across page reloads. When a user selects a theme, a CSS class gets added to the body element, and the preference saves to localStorage. The theme toggle buttons in settings reflect the current active theme.



Dark mode uses black backgrounds with light gray text, matching X's default appearance. Light mode switches to white backgrounds with dark text, with all elements—including the X logo, search bar, modals, dropdowns, and cards—receiving appropriate color overrides. The logo inverts using CSS filters to appear black against the white background.



Grok AI Chatbot
The Grok chatbot is a keyword-based assistant accessible from the left sidebar or mobile menu. It opens as a modal with a chat interface where users can type questions. The chatbot matches user input against a predefined set of keywords and returns corresponding responses. For example, asking about "explore" triggers information about the Explore page's functionality. Questions about "theme" or "dark mode" explain how to change appearance. The bot provides fallback responses when it doesn't recognize the input.



Explore Page
The Explore page showcases a dynamic media gallery featuring images and videos from external web sources. When a user navigates to Explore, the application shuffles the media items to create variety. Each item displays as a card with a title, source attribution, category tag, and the media itself. A "Refresh" button shuffles the order again, while a "Load more" button progressively reveals additional items. This feature demonstrates how the application can integrate external content while maintaining X's visual language.



Mobile Navigation
On screens smaller than 768 pixels, the layout transforms completely. The left and right sidebars disappear, replaced by a bottom navigation bar with five icons: Home, Search, Notifications, Messages, and Profile. The main feed expands to full width, and the quick chat buttons hide to avoid crowding the interface.



A swipe gesture from the left edge of the screen reveals a full navigation menu panel that slides in from the left. This panel contains all the options from the desktop sidebar: Home, Explore, Notifications, Messages, Grok, Bookmarks, Premium, Profile, and More. Users can close the menu by tapping the close button, clicking outside the panel, or swiping back.



The bottom navigation bar updates its active state based on the current page, and the search functionality remains accessible through the bottom bar's search icon, which focuses the search input and scrolls it into view.



How to Use the Application
For Desktop Users
Navigating the Interface: The left sidebar contains all main navigation options. Click any icon to access a feature—Home shows your feed, Explore opens the dynamic media gallery, and Grok launches the chatbot. The "More" button at the bottom of the left sidebar opens a dropdown with additional options including Settings.



Viewing and Interacting with Posts: Scroll through the central feed to see posts from different users. Click the heart icon to like a post—it will turn red and the counter will increase. Click the retweet icon to retweet—it turns green and the counter increments. Click the comment icon to reveal a reply box; type your reply and click "Reply" to add it to the post. Click the share icon to copy the post content to your clipboard.



Creating a New Post: Use the tweet composer at the top of the main feed. Type your content in the text area that says "What's happening?!", then click the blue "Post" button. You can also use Ctrl+Enter or Cmd+Enter as a keyboard shortcut. Your new post will appear immediately at the top of the feed.



Viewing Post Details: Click anywhere on a post except the interactive buttons or media to open the detailed modal view. This larger view shows the complete post with full content, media, engagement statistics, and all comments. You can like, retweet, reply, and share from this modal just like in the main feed.



Searching for Content: Type keywords into the search bar in the right sidebar. The feed will filter in real time, showing only posts that contain your search term in the content, username, or handle.



Changing Appearance: Click the "More" button in the left sidebar, then select "Settings and privacy." In the Display tab, choose between Dark and Light mode. Use the font size slider to adjust text size across the application. These preferences save automatically and persist when you reload the page.



Using Grok: Click the Grok icon in the left sidebar to open the chatbot modal. Type questions about the application—try asking "how do I post a tweet?" or "what is the explore page?"—and Grok will provide helpful responses based on its keyword library.



For Mobile Users
Navigating: The bottom navigation bar gives you quick access to Home, Search, Notifications, Messages, and Profile. Swipe from the left edge of the screen or tap the left edge to open the full navigation menu with all options.



Interacting with Posts: Tap the heart, retweet, comment, or share icons just like on desktop. Tap anywhere else on a post to open the detailed modal view. The experience mirrors the desktop version but with larger touch targets optimized for fingers.



Posting: Tap the composer at the top of the feed, type your content, and tap the "Post" button. On mobile, the text area automatically expands as you type.




Accessing the Menu: Swipe from the left edge of your screen at any time to reveal the full navigation panel. This gives you access to Explore, Grok, Bookmarks, Premium, Settings, and all other options from the desktop sidebar.



Closing Modals: Tap the X button in the top corner of any modal to close it, or tap outside the modal area. Pressing the device's back button or using the ESC key on a connected keyboard also closes modals.


 
 
