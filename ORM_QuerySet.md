
#-------------------------Table Structure-------------------------------------------------------
 id <br>
 brand <br>
 car_model<br>
 publish_year<br>

#----------------------------------------------------------------------------------------------

from loginapp.models import Cars  # Import a ORM

# Creating objects
<h3>Directly insert a data into database.</h3>
Cars.objects.<b>create</b>(brand='Test Car', car_model='Test Modle', publish_year='2020')

<h3>Store the data in memory and finally insert into the database.</h3>
data_save = Cars(brand='Test Car 2', car_model='Test Modle 2', publish_year='2021') <br>
data_save.<b>save</b>()

            
1.Insert a data into table & save it, Now I want to update it the brand name odi to Toyota <br>
data_save = Cars(brand='ODI', car_model='Model_3', publish_year='2022')
data_save.save()<br>

data_save.brand = 'Toyota'<br>
data_save.save()


# Retrieving objects

<h3>get method return single value, If it found no data then it make a exception also if found more than 1 data then it show's exception.</h3>
single_value = Cars.objects.<b>get</b>(publish_year=2021)

<h3>all method return all data from a table</h3>
all_cars = Cars.objects.<b>all()</b>

# filter() method
<b>Ex-1: </b> <br>Cars.objects.filter(publish_year=2021)<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (3)>]>  <b>[ 1 data found ]</b>

<b>Ex-2: </b> <br>Cars.objects.filter(brand='Pajero')<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>, <Cars: Cars object (3)>]>   <b>[ 3 data found ]</b>

<b>Ex-3: </b> <br>Cars.objects.filter(brand='Pajero', publish_year=2020)<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>]>   <b>[ 2 data found ]</b>

<b>Ex-4: </b> <br>Cars.objects.filter(brand='Pajero', publish_year=2022)<br>
<b>Output:</b> <br><QuerySet []>    <b>[ No data found ]</b>

<b>We can breakdown the Ex-4</b><br><br>
<b>Ex-5: </b> <br> Cars.objects.filter(brand='Pajero') .filter(publish_year=2020)<br>
<b>Output:</b> <br> <QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>]><br>


# exclude() method
<b>Ex-1: </b> <br>Cars.objects.filter(brand='Pajero')<br>
<b>Output:</b><br> <QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>, <Cars: Cars object (3)>]> <b>[ 3 data found ]</b>


-> <b> If we use the exclude what will be the output</b> <br>
<b>Ex-2: </b> <br>Cars.objects.filter(brand='Pajero') .exclude(publish_year=2021)<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>]> <b>[ 2 data found ]</b>

<b>Ex-3: </b> <br>Cars.objects.filter(brand='Pajero') .exclude(publish_year=2020)<br>
<b>Output:</b><br><QuerySet [<Cars: Cars object (3)>]>  <b>[ 1 data found ]</b>


# order_by() method

<b>Ex-1: </b> <br>Cars.objects.order_by('brand')    <b>[If we follow the order by parameter, we use the ' ' coma]</b><br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (4)>, <Cars: Cars object (1)>, <Cars: Cars object (2)>, <Cars: Cars object (3)>]><br>

<b>Ex-2: </b> <br>Cars.objects.order_by('brand') .filter(publish_year=2021)<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (3)>]><br>

<b>Ex-3: </b> <br>Cars.objects.order_by('brand') .exclude(publish_year=2021)<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (4)>, <Cars: Cars object (1)>, <Cars: Cars object (2)>]><br>

-> <b> Ascending order </b> <br>
<b>Ex-4: Normarl queryset</b> <br>Cars.objects.order_by('brand')<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (4)>, <Cars: Cars object (1)>, <Cars: Cars object (2)>, <Cars: Cars object (3)>]><br>

<b>Ex-4:  Ascending order queryset </b> <br>Cars.objects.order_by('-brand')<br>
<b>Output:</b> <br><QuerySet [<Cars: Cars object (1)>, <Cars: Cars object (2)>, <Cars: Cars object (3)>, <Cars: Cars object (4)>]>


# Deleting objects.

-> <b> If we want to delete one object </b> <br>
<b>Ex-1: </b> <br>Cars.objects.get(id=1).<b>delete()</b>

<b>Ex-2: </b> <br>del_data = Cars.objects.get(id=2)<br>
<b>Output:</b> <br> del_data.delete()<br>

<b>Ex-2: </b> <br> Cars.objects.filter(brand='Maroti', publish_year=2022)<br>
<b>Output:</b> <br> <QuerySet [<Cars: Cars object (15)>, <Cars: Cars object (16)>, <Cars: Cars object (17)>]>   <b>[ Found 3 data, Now want to delete the data]</b><br>
-> <b> Now I want to delete 3 data </b> <br>
Cars.objects.filter(brand='Maroti', publish_year=2022).delete()<br>
<h3>Or</h3>
del_values = Cars.objects.filter(brand='Maroti', publish_year=2022)<br>
del_values.delete()<br>

# ----------------------- QuerySet examples ----------------------------
<h3>Model example</h3>
class Address(models.Model):<br>
    id = models.IntegerField(primary_key=True)<br>
    customerid = models.IntegerField()<br>
    firstname = models.CharField(max_length=50)<br>
    lastname = models.CharField(max_length=50)<br>
    address1 = models.CharField(max_length=100)<br>
    city = models.CharField(null=True)<br>
    zip = models.CharField(null=True)<br>
<br>
queryset = Address.objects.all()<br>
str(queryset.query)


>>> queryset = Address.objects.all()
>>> str(queryset.query)      [For check the queryset to SQL query]
'SELECT "loginapp_address"."id", "loginapp_address"."customerid", "loginapp_address"."firstname", "loginapp_address"."lastname", "loginapp_address"."address1", "loginapp_address"."city", "loginapp_address"."zip" FROM "loginapp_address"'
>>>


Address.objects.filter(firstname__startswith='S')
Address.objects.filter(lastname__startswith='D')
Address.objects.filter(firstname__startswith='S') | Address.objects.filter(lastname__startswith='D')
Address.objects.filter(firstname__startswith='S').values() | Address.objects.filter(lastname__startswith='D').values()

#
from django.db.models import Q <br>
Address.objects.filter(Q(firstname__startswith='S') | Q(lastname__startswith='D'))<br>
Address.objects.filter(firstname__startswith='D', lastname__startswith='S')<br>
Address.objects.filter(Q(firstname__startswith='D') & Q(lastname__startswith='S'))<br>
Address.objects.filter(Q(firstname__startswith='A') & Q(lastname__startswith='B'))<br>.
User.objects.filter(~Q(id=2))    [~ = Note]<br>
User.objects.filter(id__gte=2)   [gte = Greaterthan equal]<br>
User.objects.filter(id__lte=2)   [lte = Less than equal]<br>

#
<h3>Union of two querysets</h3><br>
q1 = User.objects.filter(id__gte=2)<br>
q2 = User.objects.filter(id__lte=2)<br>
q1.union(q2)<br>
Hero.objects.all().values_list("name", "gender").union(Villain.objects.all().values_list("name", "gender"))<br>

Address.objects.filter(firstname__startswith='M').values('firstname')<br>
Address.objects.filter(firstname__startswith='M').values('firstname', 'lastname')<br>
Address.objects.filter(firstname__startswith="M").only('firstname', 'lastname')<br>     [only = It's return the id ]


#



