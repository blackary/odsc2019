# Using Experimentation and ML to Aid in Repayment of Micro-loans in Sub-Saharan Africa
## Brianna Schuyler - Fenix International - bschuyler@fenixintl.com

Solar panel kits

1000 employees (+4000 local salespeople who work off of commission), 600,000 
Solar Home Kits sold, 3M people impacted
- 6 countries in Sub-Saharan Africa

https://www.fenixintl.com/

Big Picture
- 1 billion people don't have access to electricity
- They could potentially leapfrog over less-ideal energy sources
    - Popular sources for light - kerosene lantern, generator, flashlight, wood
    - 10-50 cents / day
- Solar energy for ~10-20 cents per day
- Solar home systems ~$100/day won't work if you make $1-$2/day
- Instead, pay $5-10 up front, then make a payment
- Kit locks if they don't make a payment - self-collatoralizing
- Don't turn away anyone, but point people towards specific packages
- During loan repayment, customers can be difficult to reach, and have
  financial shocks
- Focusing on data is essential

Where and how to structure these contact points (SMS reminder, overdue
call, house call)?
- In person during sale
- SMS
- USSD - text-based phone menu
- Interactive voice response (IVR) if they call
- Phone call with field person
- Phone call with call center
- Service center visit
- Home visit

Call center resources are limited, so must be able to precisely target
customers who will respond well to a phone call, as opposed to an SMS

Predicting a missed first payment -- customers that miss the first payment
are more likely to default

To predict a missed first payment, include features like
- Customer occupation
- Type of ID used at sale (national ID, driver's license, passport)
- Where they first heard about solar kits
- Amount deposited
- Previous performance of the salesperson (average portfolio health)

Try a few different sklearn models, and pick out the best performing one
- happened to be a random forest

Calculating diminishing returns 
- Order customers be more likely to miss first payment
- See how fast the number of false positives increases as we go deeper in
  the list

Run an experiment of likely-to-miss people, and call some and don't call
others

Lessons learned
- Do a trial run
- Make sure everyone knows what you're doing and why
- Increase awareness of non-parametric tests 

Iterate on model/experiment
- Include new features to predict missed first payment (e.g. how well
  device is performing)
- Try new education scripts
- Periodically measure model performance and ROI to make sure the
  interventions are still worth it
- Head into the field for new ideas

Hybrid model - create list of customers who:
- are likely to miss their first payment
- will likely pay if called
- will likely not pay if not called
- A/B test -- what is the decerease? Is it worth the cost?
- Iterate and try in different markets
