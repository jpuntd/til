# passing command line arguments to npm script

We want to run the test:library script but also output coverage report. Jest has a `--coverage` flag.  
Use:

    npm run test:library -- --coverage

The extra -- is needed to separate the arguments passed to npm command itself from arguments passed to your script.
