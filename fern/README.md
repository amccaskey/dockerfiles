# Fern Docker Image Build

To build this image execute the following command:

```bash
docker build -t eclipseice/fern .
```

To run Fern from the command line with a local input file:
```bash
docker run -v /path/to/data:/fern/data eclipseice/fern sh -c "fern-exec /fern/data/alpha.ini"
```
