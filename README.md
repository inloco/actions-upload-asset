# Upload Assets Action

## Example

```yaml
permissions:
  id-token: write # required
jobs:
  one:
    steps:
      - run: docker save -o images.tar
      - uses: inloco/actions-upload-assets@HEAD
        with:
          name: docker-images
          path: images.tar
  two:
    needs: one
    steps:
      - uses: inloco/actions-download-assets@HEAD
        with:
          name: docker-images
      - run: docker load -i images.tar
```
