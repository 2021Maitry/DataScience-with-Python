# DataScience-with-Python
Python Project - Churn Emails
#We have a text file which records mail activity from various individuals in an open source project development team. Below is the file location

#/cxldata/datasets/project/mbox-short.txt
To see the first 15 lines of mbox-short.txt, please use below command on the console(from jupyter notebook)
!head -n 15 /cxldata/datasets/project/mbox-short.txt
def number_of_lines():

    fhand = open('/cxldata/datasets/project/mbox-short.txt')
    inp = fhand.read()
    fhand.close()
    count = 0
    for c in inp:
        if c=='\n':
            count +=1;
    return count
print(number_of_lines())

#Write a function count_number_of_lines which returns the count of the number of lines starting with Subject: in the file
    
  def count_number_of_lines():
    
    fhand = open('/cxldata/datasets/project/mbox-short.txt')
    count = 0
    for line in fhand:
        line = line.rstrip() # Remove new line characters from right
        if line.startswith('Subject:'):
            count +=1
    return count
 
 print(count_number_of_lines())
 
 #Define a function average_spam_confidence which calculates the average spam confidence and returns it
 def average_spam_confidence():
 
    with open('/cxldata/datasets/project/mbox-short.txt') as f:
        count = 0
        spam_confidence_sum = 0
        for line in f:
            line = line.rstrip() # Remove new line characters from right
            if line.startswith('X-DSPAM-Confidence:'):
                var, value = line.split(':')
                spam_confidence_sum = spam_confidence_sum + float(value)
                count = count + 1
    return spam_confidence_sum/count
    print(average_spam_confidence())
    
   # Write a function to find which day of the week the email ws sent?
   def find_email_sent_days():
    daysdict = {}
    dayslist = []

    with open("/cxldata/datasets/project/mbox-short.txt") as f:
        for line in f:
            dayslist = line.split()
            if len(dayslist) > 3 and line.startswith('From'):
                day = dayslist[2]
                if day not in daysdict:
                    daysdict[day] = 1
                else:
                    daysdict[day] += 1
    return daysdict
    print(find_email_sent_days())
    
# Count number of messages from each email address
def count_message_from_email():

    lineslist=[]
    emaildict={}
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
      for line in f:
        lineslist = line.split()
        if line.startswith('From:'):
          email=lineslist[1]
          if email not in emaildict:
            emaildict[email] = 1
          else:
            emaildict[email] += 1
    return emaildict
    
  # Count number of messages from each domain
  def count_message_from_domain():
  
    lineslist=[]
    domaindict={}
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
        for line in f:
            lineslist = line.split()
            if line.startswith('From:'):
                email=lineslist[1]
                domain = email.split('@')[1] 
                if domain not in domaindict:
                    domaindict[domain] = 1
                else:
                    domaindict[domain] += 1
    return domaindict
