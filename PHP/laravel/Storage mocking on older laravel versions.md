# Storage mocking on older laravel versions

```php
function makeStorageMock()
{
    $fileSystemMock = Mockery::mock(\Illuminate\Contracts\Filesystem\Filesystem::class);

    $storageMock = Mockery::mock('alias:' . \Illuminate\Support\Facades\Storage::class);
    $storageMock->shouldReceive('disk')
        ->with('s3')
        ->andReturn($fileSystemMock);

    return $fileSystemMock;
}

$storage = $this->makeStorageMock();
$storage->shouldReceive('delete')
    ->with($job->getStoredFilename())
    ->andReturn(true)
    ->once();
```
