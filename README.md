# python
#!/usr/bin/python
def leap( year ):
    "checks whether a year is leap year or not"
    last = year % 100
    if (last==0):
        check = year % 400
    else:
        check = year % 4
    if check == 0:
        return 1 
    else : return 0
def validity(date, month , year,leap):
    "check whether the given input is valid or not"
    odd = [1,3,5,7,8,10,12] # month with 31 days
    even = [4,6,9,11] # month with 30 days
    if year > 1581 and month > 0 and month < 13 and date > 0 and date < 32:
            if month in odd and date < 32:
                return 1    
            elif month in even and date < 31:
                return 1
            elif month == 2 :
                if leap == 1 and date < 30:
                    return 1
                elif date < 29:
                    return 1
                else: return 0
            else:
                return 0;
    else:
        return 0;
def calc(date,month,year,first):
    "return day"
    cur_year = year - 1
    last = cur_year % 100
    front = int(cur_year/100)
    print "last" + str(last)
    print "front"+str(front)
    fixed = [3,1,-1,-3]
    i = front%4
    print 'leap pattern' + str(i)
    second=((last/4)%7)
    print 'second'+str(second)
    third=(last%7)
    print 'third' +str(third)
    print 'fixed'+str(fixed[i])
    tot= first+fixed[i]+second+third
    print 'tot'+str(tot)
    bookmark = [0,3,28,0,4,9,6,11,8,5,10,7,12]
    if first == 1:
        bookmark[1]+=1
        bookmark[2]+=1
    book_date = bookmark[month]
    print "book_date" + str(book_date)
    if(book_date >= date):
        diff = book_date - date
    else:
        diff = date - book_date
    print "diff " + str(diff)
    final = tot + diff
    final%=7
    print 'final'+str(final)
    return final    

date = input("enter the date")
month = input("enter the month")
year = input("enter year")
first = leap(year) # return 1 if valid
print first 
v = validity ( date,month,year,first ) #return 1 if valid
print v
day = ['sunday','monday','tuesday','wednesday','thursday','friday','saturday']
op = calc(date,month,year,first)
if validity == 1:
    print "your input data is not valid yet your output is..."
print "Here Your Day: "day[op]
















    
