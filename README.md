# Drupout

Drupal module to create Speakout campaigns from a webform.
After inserting the submission into DB, the module calls the Speakout API
to clone a template and replace some variables in that template.

## Setup
### API user
The module requires a Speakout user, which will be used to connect to the API.
The credentials of the user can be set in the admin form.

### Templates
The ID of the campaign to clone is determine from the language picked by the member
and the variable `drupout_speakout_template`, which can be modified in the admin form.
The variable should be a comma-separated list of pairs `ll:xxx` where ll is the language code 
and xxx is the corresponding template ID.

This variable is exposed as a webform options set, so the available languages can be 
dynamically determined from the configuration. 

The module accepts that the selected language is not present in the variable
`drupout_speakout_template`, in which case the Speakout campaign is simply not created.

## How the Speakout campaign is created
If the selected language is supported, the matching Speakout template is cloned,
and some of the fields are replaced by the form values. Moreover, some fields are
modified by replacing tokens with form values. For example, the value of the field
`why_is_this_important` is sent in the JSON property `variables.sign_advice.why_important`,
which means that Speakout will replace the token `{why_important}` in the sign advice
with the value of the field `why_is_this_important`.

See the function `drupout_form2json` for the details of how each form field is used.
