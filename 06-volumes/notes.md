# Kubernetes Volumes

A Volume is a way for containers in the same Pod to share data.

Normally, each container has its own filesystem. If a container restarts, anything stored inside it is lost. A Volume gives the containers a shared place to read and write files.

In the example, both the writer and reader containers mounted the same Volume at `/data`. The writer created a file, and the reader was able to read that same file because they were using the same Volume.

The `emptyDir` volume type creates an empty directory when the Pod starts. It exists for as long as the Pod is running. If the Pod is deleted, everything inside the `emptyDir` is lost.

So:

- Containers in the same Pod can share data through a Volume.
- `emptyDir` is temporary storage.
- For data that must survive Pod deletion, use Persistent Volumes (PV/PVC).