# Resource Acquisition Is Initialization (RAII)

- couples the use of a resource to the lifetime of an object
    - Acquisition of the resource happens with the initialization (i.e. construction) of the object
    - the destruction of that object releases the resource.
- `std::unique_ptr<T>`: the resource in question is an object allocated on the heap

Example: explicite return of resource dangerous because of exception or return statements
```c++
void AppendToContent(absl::string_view to_append) {
   mutex_->Lock();
   absl::StrAppend(content_, to_append);
   mutex_->Unlock();
}
```

With RAII, return of resource is guarenteed, when leaving the containing block
```c++
void AppendToContent(absl::string_view to_append) {
   absl::MutexLock lock(&mutex_);
   absl::StrAppend(content_, to_append);
} // MutexLock destructor runs here, calling mutex_->Unlock().
```
