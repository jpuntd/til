# Understand reset 

The reset command overwrites these three trees in a specific order, stopping when you tell it to:

1. Move what the branch HEAD points to (stop here if --soft)
2. Make the stage look like HEAD (stop here unless --hard)
3. Make the working directory look like the stage

[Source](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified). 
