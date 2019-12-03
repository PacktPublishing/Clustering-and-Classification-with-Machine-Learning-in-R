####################################################################
######## read in data from google sheets
## a public google sheet
##https://docs.google.com/spreadsheets/d/1X85PgCqavImGZPGdbrEfQc6uzNP98KXwZcf-8JsKZto/edit#gid=8983842

library(googlesheets)
gs_ls()

# get the Britain Elects google sheet
be = gs_title("Britain Elects / Public Opinion")

# list worksheets
gs_ws_ls(be)

# get Westminster voting
west = gs_read(ss=be, ws = "Westminster voting intentions", skip=1)

# convert to data.frame
wdf = as.data.frame(west)

head(wdf)

