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

