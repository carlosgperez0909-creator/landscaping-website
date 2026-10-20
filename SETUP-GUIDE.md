# Your landscaping website: setup guide

This takes about 20–30 minutes, one time. You don’t need to write any code. Netlify and GitHub occasionally rename buttons, so if a label looks slightly different, look for the closest match.

## What’s in the folder

- `index.html` is the public website: services, photo gallery, a proposal request form, and a site-walk scheduling form for HOA boards and property managers.
- `thanks.html` is a backup “request received” page.
- `content/` holds your editable text, services, and gallery list. You’ll edit these through the admin page, not by hand.
- `images/uploads/` is where your photos go. It holds four sample images for now.
- `admin/` is your private editing page.

---

## Step 1: Put the files on GitHub

GitHub stores your website files, and every edit you make in the admin page gets saved here.

1. Go to **github.com** and create a free account.
2. Click **+** (top right) → **New repository**. Name it something like `landscaping-website`. Choose **Private**, then click **Create repository**.
3. On the next screen, click **uploading an existing file**.
4. Unzip the folder I gave you. Open it, select **everything inside it** (index.html, admin, content, images, and the rest), and drag it into the browser window. Don’t drag the outer folder itself.
5. Click **Commit changes**.

## Step 2: Put the site online with Netlify

1. Go to **netlify.com** and click **Sign up**, choosing **Sign up with GitHub**.
2. Click **Add new project** → **Import an existing project** → **GitHub**, then pick your repository.
3. Leave the build settings empty and click **Deploy**.
4. After a minute you’ll get a web address like `something-random.netlify.app`. Your site is live. You can rename it under **Project configuration → Change project name**.

## Step 3: Turn on the quote and booking forms

1. In Netlify, open **Forms** in the left menu and click **Enable form detection**.
2. Go to **Deploys** → **Trigger deploy** → **Deploy project**. This lets Netlify find your two forms. In Netlify they’re named “quote” (proposal requests) and “booking” (site walk requests).
3. To get an email for every request, go to **Project configuration → Notifications → Emails and webhooks → Form submission notifications → Add notification → Email notification**. Enter your email address and choose “Any form”.

Test it by submitting a proposal request on your live site. It should appear under **Forms** in Netlify.

## Step 4: Set up your admin page

This step lets you log in at `yoursite/admin` with your GitHub account.

**4a. Tell the admin page where your files live.**
1. On GitHub, open your repository → `admin` folder → `config.yml` → click the pencil icon.
2. Change this line:
   `repo: YOUR-GITHUB-USERNAME/YOUR-REPO-NAME`
   to your real details, for example:
   `repo: janesmith/landscaping-website`
3. Click **Commit changes**.

**4b. Create a GitHub login key.**
1. On GitHub, click your profile photo → **Settings** → **Developer settings** (bottom of the left menu) → **OAuth Apps** → **New OAuth App**.
2. Fill in:
   - Application name: `My website admin`
   - Homepage URL: your Netlify address, like `https://your-site.netlify.app`
   - Authorization callback URL: `https://api.netlify.com/auth/done`
3. Click **Register application**, then **Generate a new client secret**. Keep this page open, because you’ll need the **Client ID** and **Client secret**.

**4c. Give the key to Netlify.**
1. In Netlify, go to **Project configuration → Access & security → OAuth**.
2. Click **Install provider**, choose **GitHub**, and paste the Client ID and Client secret.

**4d. Log in.**
Visit `https://your-site.netlify.app/admin` and click **Sign in with GitHub**. You’re in.

---

## Day-to-day: running your website

**Seeing proposal and site walk requests.** Open Netlify → **Forms** → click **quote** (proposal requests) or **booking** (site walks). Each request shows the community name, contact person and their role, phone, email, number of homes, when their current contract ends, and their notes. You can delete old ones, mark junk as spam, or download them all as a spreadsheet (CSV). Spam is filtered automatically.

**Editing services and prices.** Go to `/admin` → **Website content → Services & prices**. The price line can say anything, like “Monthly contract” or “From $150 per month”. You can add, remove, reorder, or edit services, then click **Save**. The live site updates in about a minute.

**Adding or removing gallery photos.** Go to `/admin` → **Photo gallery**. Click **Add Photo**, upload a picture, add a caption, and save. To remove a photo, delete it from the list and save. Replace the four sample images with your own work as soon as you can.

**Changing your business name, phone, hours, and so on.** Go to `/admin` → **Business info**. This is also where you edit the three “why communities choose you” points.

**Site walks.** Board members or managers request a date and time window and a meeting spot. You confirm by phone or email, walk the property, then send your written proposal. If you later want them to pick open slots straight from your calendar, a tool like Calendly can be added.

## Using your own domain name

In Netlify, go to **Domain management → Add a domain**. You can buy one there or connect one you already own (from GoDaddy, Namecheap, etc.). Netlify adds the secure padlock (HTTPS) for you. After that, update the Homepage URL in your GitHub OAuth App to the new address.

## Costs

GitHub and Netlify both have free plans that comfortably cover a typical small-business site. Netlify’s free plan has monthly usage limits, so check their pricing page if your site gets very busy. A domain name is usually about $10–20 a year.
