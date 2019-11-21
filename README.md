# new-website

Initial document for the new [belfastelixir.org](https://www.belfastelixir.org)
website.

## Premise

We want to build a new website for the belfast elixir meetup group for several
reasons:

- [meetup.com](https://www.meetup.com) are now starting to
  [charge](https://www.theverge.com/2019/10/15/20893343/meetup-users-furious-new-rsvp-payment-test)
per RSVP.

- The site is currently just a blog, written in jekyll. It is no longer
  actively maintained.

- We want to add new sections/features to the site that will enhance the
  website for both users and admins easily, which requires more than a 'markup
blog'

## What are the features you want?

We want to replace meetup. Meetup is really, at the guts of it - a website that
allows you send out emails to a particular group and for the recipients to RSVP
to the aforementioned meetup.

So with that thinking (this is up for discussion), we would like the following:

- Several 'static' pages:

  - Home 
  - About Us
  - Code of Conduct 
  - Contact Us
  
- A blog to document each meetup with content via links or integrations to our
  social media channels.

- A blog (or a section of the blog promoted to top level status) for "Today I
  learnt"

- A RSVP page that requires a uniqueid that allows a member to say "yes" or
  "no" to a meetup email

- Unsubscribe page that requires a uniqueid that allows a member to unsubscribe
  from the email list. 

- An admin section

  - Show the status of members coming to the meetup
  
  - Able to send out a bulk email to members for a meetup

### Several Static Pages

Nothing fancy - just pages that don't need to be dynamically generated
everytime.

### Blog

Simple blog that allows an article to be pushed to the site if a certain status
is given.  Should use some sort of SEO friendly URI.
 
### Blog (TIL section)

Same as the blog above (might even make sense to have it as a sub section of
the blog but have it 'promoted' in some way. It should be a top level section
to the front end.

### RSVP page

A simple 'yes' or 'no' choice given to the user. Uniqueid should tell us the
user and the meetup in question.

### Unsubscribe Page

A simple page that takes a uniqueid and automatically unsubscribes users from
the mailing list. 

### Admin Section

An admin section

#### Meetup Pages

##### index page

A list of meetups in descending date order. Summary information should include:

  - Meetup date (link to meetup page?)
  - Meetup Title (link to meetup page?)
  - # going/went
  - # no going/declined 
  - # no reply
  - # sent

##### Individual Page

  - List of members that went
  
##### Bulk email page

Able to send out a bulk email to members that are subscribed

## Questions

1. What is our MVP for this app?

2. We need to discuss the features first and iron them out.

As this is a meetup we don't want to spend much time talking about what we are
going to do. This is the reason for the README, it can be amended on the fly. 

There is enough in this document to facilitate a meetup and to start coding a MVP. 
 
### Russell opines

1. Event app MVP

A way to add new event pages and allow members to say that they are attending.
* Event pages can be added manually and use Markdown syntax for formatting
* Members can add their name to a list without any authentication system

2. Event app post-MVP features

#### Permissions / Authorization system

* Admin Super-user
  * Allowed to perform administrative functions (detailed below)
* Mailing List admin
  * Can create a new mailing list
    * Can assign ownership of a mailing list
  * Can remove any mailing list member
  * Can delete any mailing list
* Mailing list owner
  * Can remove members from a mailing list they own
  * Can email members of a mailing list they own
  * Can delete a mailing list they own
* Editor
  * Blog admin
  * Can edit any blog entries
* Author
  * Can create a blog
  * Can create blog entries or edit an entry they created
* Super-organiser
  * Can edit any event
  * Can email attendees of any event
* Organiser
  * Allowed to create a new event or edit an existing event they created
  * Allowed to email those who have registered interest in their event
* Member
  * Can attend or not attend an event
  * May say that they are interested in attending an event
  * May add additional information, if requested on event (e.g., dietary
    or accessibility requirements)
  * Can opt in or out of mailing lists

##### User / Authentication system

* Register user
  * This should use verification to prevent abuse (probably the standard 
    generate token / send via email / authorise account when request is 
    received with a valid token)
  * Requires an email address and password
  * May create a username alias (will default to email address as username)
* Login
  * Username / password
  * 2FA
* Forgot password
  * No information disclosure re: whether an account email exists
* Profile page
  * May edit fields, as specified globally by admin
  * Freeform, Markdown formatted, "about me" section

#### Blogs

For Editor accounts:

* Has Author permissions for blogs they do not own

For Author accounts:

* Can create a blog
* Can edit blog metadata
* Can create, edit, delete a blog entry that they own or 
  have edit permissions on
* Can delete a blog they own

#### Mailing lists

For List admin:

* Has List owner permissions for lists they do not own
* Can edit members and roles for a list

For List owner:

* Can create a new list
* Can edit list description
* Can view list subscribers
* Can remove a member from a list they own or have permissions on
* Can delete a list they own

For List member:

* Can subscribe or unsubscribe to a list
* Will receive emails for that list

#### Events

For organisers:

* Create event
  * Date / time
  * Location
  * Title
  * Description
  * Additional information required from attendees (e.g., dietary or
    accessibility requirements)
* Edit event
  * Edit fields listed above
  * Additional note (date/time stamped on event page)
* Delete event

All others:

* View event detail
  * Details as per Events above
  * List of attendees
* View event summary
  * Short version, for widget use

#### Admin system

* User management
  * Add / edit / delete user
  * Manage permissions
  * Fields requested on user profile page

