- 👋 Hi, I’m @Shafag225
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Shafag225/Shafag225 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
 blaggacao commented on Jun 5 • 
I'm seeking advice on a long-held consideration to amend the OCI image spec with means to add an infinite number of content==location-addressed blobs to the file system.

Let's call these "Nix Store Paths", that reside in a special place on the (linux) filesystem under /nix/store/<hash>-<name>.

Because of the content hash being part of the location address, location and content adressess become interchangeable and conflicts in the location-address space never occur.

Hence, no "merging" is required, no overlay filesystem, and above all, no layer limit, which sets the stage for arbitrary deduplication.

Wait a sec; how so? Doesn't linking expect well-known location-addresses?

The trick why this works is that the ELF binaries are patched so that all linking is redirected to corresponding /nix/store/... paths, but that's an implementation detail and shall solely make this proposal plausible (for ELFs).

The two porposed mime types would "read" as follows:

application/vnd.nix.store.path.v1.nar
application/vnd.nix.store.path.v1.nar+gzip
