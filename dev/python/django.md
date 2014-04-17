### Namin standards

Urls:

`catalogue:product_edit`
`catalogue:product_list`

Views:

`UserListView`
`ProfileEditFormView`


-----------


####Formlarda fieldlarin sirasini belirleme

`````python
class MyCustomForm(forms.Form):
    def __init__(self, *args, **kw):
        super(MyCustomForm, self).__init__(*args, **kw)

        api_token = forms.CharField(label=_("Token"), ...)
        self.fields['api_token'] = api_token

        self.fields.keyOrder = [
            'username',
            'email',
            'api_token',
            'password',
        ]
        
`````
