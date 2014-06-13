The sensible data keys are:

# all
#-------------------------------------------------------------------------------
supervisord_http_user: admin
supervisord_http_pass: xxxxx


# dbservers
#-------------------------------------------------------------------------------
postgresql_users:
  - name: "postgres"
    pass: "xxxx"
    host: "localhost"
    encrypted: no
  - name: "favorshare"
    pass: "xxxx"
    host: "*"
    encrypted: no

