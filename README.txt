Notes on aadl_holds.csv

AADL Holds Data
July 1, 2014�June 30, 2015
Containing 969,495 lines

Thanks for downloading this dataset! These are records forcibly extracted
from AADL's Integrated Library System (ILS), called Innovative Millennium,
which is a big black box that runs the library circulation process. We are
exploring open source ILS alternatives, but for now, we're using this staid
but stable product that has some blemishes that would make any Hacker blush
in sympathetic embarrassment. You'll see some of those in this dataset. But
for now, here are details on what this file contains and what its contents
mean.

Requests are when a library user requests that an item be retrieved from the
shelf at any of AADL's 5 locations, and sent to their desired pickup location
at any one of AADL's 5 locations. If no copies are available, their request
will be queued in order received for the next available copy that is
returned. The data in this set is retrieved nightly from the ILS and a row
is created for each request that was placed that day. When the request is
fulfilled, meaning when the item is placed on the hold shelf for pickup by
the requester, the row is updated to show that the request has been filled.
This dataset contains no information about the requester or their pickup
point.

The file contains about 1 Million rows, each with these fields in this order:

7-digit number: Bib record number. The number of the title (bibliographic)
record in AADL's catalog. You can reach the web version of the catalog
record for a given bib using this URL
scheme: http://aadl.org/catalog/record/(bibnumber) and you can get a bit of
machine-readable metadata for the item data via rss
athttp://aadl.org/cata/record/(bibnumber)?output=rss for example:
http://www.aadl.org/catalog/record/1388165
or
http://www.aadl.org/catalog/record/1388165?output=rss

Hexadecimal string: A hash of the user id.

Date: The date the request was placed. YYYY-MM-DD.
single letter: Material code, like book, dvd, bluray, cd, map, tool,
etc. Here's a table:
	a=BOOK
	b=BOOK ON TAPE
	c=MUSIC SCORE
	f=AV LANG STUDY
	g=DVD
	i=BOOK ON CD
	j=CD
	k=KIT
	l=LARGE TYPE
	m=CD-ROM
	p=ART PRINT
	r=TOOLS
	t=CASSETTE
	z=EBOOKS
	v=VHS
	s=MAGAZINE
	x=GRAPHIC NOVEL
	u=BLU-RAY
	e=MAP
	n=NEWSPAPER
	w=MICROFILM
	y=WEBSITE
	q=STREAM
	Some of these are not requestable and will not show up in the dataset.

Date: Date the request was filled by the system, YYYY-MM-DD. Null (\N) if
the request is still outstanding. If this date is present and the cancel
status field (see below) is Null, that means the request was filled and
placed on the holdshelf for pickup on that date. If the fulfillment date is
present and the cancel status field is not null, that means the request was
canceled on that date.

Number: Number of copies of that title owned by AADL at the time the request
was placed. A value of 0 means that the request was placed before any AADL
copies arrived.

Letter: Location of the request's pickup point:
	d: Downtown Library
	m: Malletts Creek Branch
	p: Pittsfield Branch
	t: Traverwood Branch
	w: West Branch

Text: Cancel Status Field. In most rows, this will be Null. That means the
hold was filled normally and picked up. There are a few other kinds of
values for this field. As mentioned above, if this field is not null, it
contains the cancellation source, and the second date field on that row is
the date of cancellation. Here are the other known values of this field:
	clearholdshelf: this hold was cleared by the clearholdshelf report,
	meaning it was not picked up from the holdshelf by the patron during the 6-
	day pickup window and was cancelled and sent along to the next person, or
	back to the shelf.
	milacq*: cancelled by staff on the acquisitions team. Usually items
	they called back for relabeling, or holds on items that never were shipped,
	etc.
	milcirc*: cancelled by staff in the circulation department. Either
	because the patron requested in person or over the phone to cancel their
	request, or because the request cannot be filled (because the items are all
	missing or out of print, etc)
	milcat*: cancelled by staff on the cataloging team. Usually because
	they're merging records and have re-created the requests on the new record.
	milmyselfcheck: cancelled by the requesting user at the selfcheckout
	stations.
	webpac*: cancelled by the requesting user over the web.

That's what there is to know about this dataset! Please enjoy and let us
know what you do with the data or if you have any questions or ideas; you can
reach me at drozda@aadl.org.

Now go get a library card if you don't have one already so your requests can
join these millions!