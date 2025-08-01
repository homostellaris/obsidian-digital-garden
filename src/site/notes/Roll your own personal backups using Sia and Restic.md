---
{"dg-publish":true,"permalink":"/roll-your-own-personal-backups-using-sia-and-restic/","tags":["tech","backup"]}
---

I've found Sia to be far too unstable. Since running the renter desktop app I've encountered about 10 issues, all of which have eventually been solved by an update (so not user error). I really want to support the project because it can offer great redundancy and cost efficiency but I don't have time to be constantly on their Discord working to diagnose issues.

I've therefore moved to Wasabi as its well-recommend and S3 compatible so barely any tweaks to my backup scripts needed. I may try Sia again in future.

---
I have managed to get very cheap (will give a more accurate number later but about 3 dollars per terabyte) highly redundant backups of my personal data using the decentralised Sia network to backup my encrypted Restic repos.

I will make this guide much more comprehensive when the dust has settled and I have time but at a high-level the steps are:
1. Install restic
2. Install renterd
	1. I installed the desktop app on my Windows machine as I couldn't be bothered to learn the CLI.
3. Purchase Siacoin (I used https://www.kraken.com/).
	1. Wait for holds
	2. Transfer crypto to renter wallet
4. Create a bucket
	1. Ensure that the S3 interface is enabled in your renterd settings.
5. Run Restic commands on a schedule to backup data directly to Sia via the S3 interface.
	1. I actually backup to a Restic repository on an external hard drive first and then use Restic's `copy` command targeting renterd's S3 URL as there are some advantages to doing it this way if you wish to maintain both local and remote backups.

---
# How I got here
My data are probably my most valuable possessions as they are the only things I can't replace. Ever since I learned of the possibility of cloud backup solutions I've been set on using them but always found good consumer solutions for personal backups lacking.
## CrashPlan
This feeling was reinforced when my provider CrashPlan discontinued their personal product offering in order to double-down on their enterprise product.
## Spideroak
After CrashPlan I spent a while Googling alternative solutions and settled on Spideroak. I found the product to be clunky and unreliable and stopped using it after a while.
## Restic
Feeling somewhat disillusioned, I discovered an excellent command-line tool called [Restic](https://restic.net/). It would require more of my own effort to get something usable with this but by this point I was OK with that.

I have a desktop PC running Windows that I also use as a Plex Media Server and the 'master' place to store all my precious data. I used Task Manager and a Powershell script to setup a scheduled task to backup my files to a Restic repo in Google Cloud storage and email me the resulting logs every morning.
## Egress fees
I felt very smug that I had managed to roll my own simple but reliable personal backup system that also seemed very cheap - I was paying about $0.69/month to store 300GB in coldline storage buckets compared to about $8/month with commercial offerings.

However I'd foolishly overlooked how much it would cost me to download my backup in the case of a disaster. I don't mean the read fees for using a coldline bucket instead of a standard bucket. I mean the general egress fees for all data transfer out of Google Cloud Storage.

It was going to cost me about $100 to download those 300GB if I ever needed to. I thought I must be calculating the costs wrong but I learned that cloud providers aggressively lower their ingress fees to drive adoption whilst simultaneously charging hard for egress to discourage leaving and because egress generally means you are serving data to customers and making money.

In retrospect this makes complete sense and I don't blame cloud providers for doing this - in fact its smart. But it did make GCP entirely unsuitable for personal backups in my opinion.
## Sia
Now my entirely unpractical and convoluted plan is to use this as an excuse to explore the world of decentralised apps & crypto by renting some storage on the Sia network and updating my using that as the backend for Restic instead.

I already discovered a gotcha with this as the minimum 'block' size on the Sia network is 40MB which means that you end up being charged significantly for lots of small files you're likely to find in a personal backup.

However they're just on the cusp of releasing new components which include 'packing' features which automatically pack files into 40MB blocks for you.

More updates to come as I work on this.