## Autoload
- All the subdirectories of app will by default be autoloaded
- Any 2nd level sub-directories app/*/concerns will be automatically loaded

See: http://guides.rubyonrails.org/autoloading_and_reloading_constants.html

## General Configurations
- config.exceptions_app: handle uncaught exceptions raised in controller \
  e.g. `config.exceptions_app = routes`
  
See: http://guides.rubyonrails.org/configuring.html#rails-general-configuration
