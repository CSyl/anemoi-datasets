Findings:

- Through the current main code able to read s3 files IF setting up configuration in the kerchunk-zarr format. This requires one to consolidate all the meta/attributes of each variables into a single JSON file. The JSON file must be set in the configuration prior to a anemoi dataset creation. There is only a feature to generate this JSON for NETCDF & GRIB files (NOT ZARR).

When testing to see if a zarr in a S3 bucket can be converted to anemoi format via the latest anemoi-dataset package AND anemoi-dataset develop branch, unable to extract metadata and convert to json, which results in an empty MultiFieldList()

__ON ZARR within S3:__
- When setting up the configuration file for a zarr located in S3, obtain an error regarding an empty MultiFieldList() when using the S3 URL (s3://noaa-ufs-gdas-pds/test_ar.zarr) and when the HTTPS URL (https://noaa-ufs-gdas-pds.s3.amazonaws.com/test_ar.zarr) in the configuration file. When  Thus, cannot obtain the entire json of a zarr when calling its S3 nor HTTPS URL in config. file.

- When executing the open_dataset.py within the anemoi-dataset develop branch, 'data' feature in the dataset could not be found, but when adding a dummmy data variable overrided error and another error resulted with: inability to obtained a JSON due to a JSON decoding error 

__ON ZARR within GCP:__
- When setting up the configuration file for a zarr located in GS, obtain an error regarding the inability to connect to the GCP server when using the GS URL (gs://gcp-public-data-arco-era5/ar/1959-2022-1h-360x181_equiangular_with_poles_conservative.zarr) and inability to obtained a JSON due to a JSON decoding error when using the GCP HTTPS URL w/in the configuration file. Thus, cannot set url as the path of an GS nor its HTTPS to a zarr file.

- When executing the open_dataset.py within the anemoi-dataset develop branch, 'data' feature in the dataset could not be found.



TODO:
1) Test to SEE IF tests/xarray/test_zarr.py method, test_inca_one_date(), allows one to generate a JSON of metadata
2) NEED TO SETUP GCPSTORE IN FLAVOUR.PY, COORDINATES.PY

3) TEST the test_kerchunk print("CHECK HERE ON THE JSON & HOW IT LOOKS PRIOR TO IT BEING ADD WITH MULTIZARRTOZARR", jsons)
& then, NEED TO SETUP A WAY TO consolidate all the meta/attributes of each variables of a ZARR file into a JSON file. 

4) Test if a zarr in a S3 bucket can be converted to anemoi format via the latest anemoi-dataset package AND anemoi-dataset develop branch. Conclusion:  With anemoi-dataset latest version, results in an empty MultiFieldList(). With anemoi-dataset develop branch, unable to extract metadata and convert to json due to JSONDecodeError: Expecting value: line 1 column 1 (char 0). Note: 'data' feature in the dataset could not be found, but to get around this a data variable was added to the zarr store in cloud to override error.

> With anemoi-datasets create
- ** Result: ** 
(anemoi_test)     anemoi % anemoi-datasets create test_s3_zarr.yaml test_s3_zarr.zarr
2024-09-16 11:15:58 INFO Task init((),{}) starting
2024-09-16 11:15:58 INFO Setting flatten_grid=True in config
2024-09-16 11:15:58 INFO Setting ensemble_dimension=2 in config
2024-09-16 11:15:58 INFO Setting flatten_grid=True in config
2024-09-16 11:15:58 INFO Setting ensemble_dimension=2 in config
2024-09-16 11:15:58 INFO {'start': datetime.datetime(2021, 12, 31, 9, 0), 'end': datetime.datetime(2021, 12, 31, 15, 0), 'frequency': '1h', 'group_by': 'monthly'}
2024-09-16 11:15:58 INFO Groups(dates=1)
2024-09-16 11:15:58 INFO FunctionAction: url=s3://noaa-ufs-gdas-pds/test_ar.zarr param=2m_temperature level=[1000] 
2024-09-16 11:15:58 INFO Minimal input for 'init' step (using only the first date) :
2024-09-16 11:15:58 INFO xarray-zarr(['2021-12-31T09:00:00'])
2024-09-16 11:15:58 INFO Config loaded ok:
2024-09-16 11:15:58 INFO Found 7 datetimes.
2024-09-16 11:15:58 INFO Dates: Found 7 datetimes, in 1 groups: 
2024-09-16 11:15:58 INFO Missing dates: 0
2024-09-16 11:15:59 WARNING No data found for s3://noaa-ufs-gdas-pds/test_ar.zarr and dates ['2021-12-31T09:00:00'] and {'param': '2m_temperature', 'level': [1000]}
2024-09-16 11:15:59 WARNING Options: {}
['valid_datetime', '2021-12-31T09:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T10:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T11:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T12:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T13:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T14:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T15:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T16:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T17:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T18:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T19:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T20:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T21:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T22:00:00', 'param', '10m_u_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T09:00:00', 'param', '10m_v_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T10:00:00', 'param', '10m_v_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T11:00:00', 'param', '10m_v_component_of_wind', 'level', 'None']
['valid_datetime', '2021-12-31T12:00:00', 'param', '10m_v_component_of_wind', 'level', 'None']
Traceback (most recent call last):
  File "  /miniconda3/envs/anemoi_test/bin/anemoi-datasets", line 8, in <module>
    sys.exit(main())
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/__main__.py", line 24, in main
    cli_main(__version__, __doc__, COMMANDS)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/utils/cli.py", line 135, in cli_main
    cmd.run(args)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 64, in run
    self.serial_create(args)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 74, in serial_create
    task("init", options)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 29, in task
    result = c.run()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/__init__.py", line 355, in run
    return self._run()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/__init__.py", line 375, in _run
    variables = self.minimal_input.variables
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 480, in variables
    self.build_coords()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 431, in build_coords
    from_data = self.get_cube().user_coords
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 238, in get_cube
    cube = ds.cube(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/earthkit/data/core/fieldlist.py", line 1491, in cube
    return FieldCube(self, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/earthkit/data/indexing/cube.py", line 55, in __init__
    assert len(ds), f"No data in {ds}"
AssertionError: No data in MultiFieldList()

> With anemoi-datasets develop branch
- from __init__ import add_dataset_path
- from __init__ import open_dataset
- ds2 = open_dataset("s3://noaa-ufs-gdas-pds/test_ar.zarr")
- ** Result: ** 
---------------------------------------------------------------------------
JSONDecodeError                           Traceback (most recent call last)
Cell In[3], line 9
      3 from __init__ import open_dataset
      5 #add_dataset_path("https://object-store.os-api.cci1.ecmwf.int/ml-examples/")
      6 
      7 # import time
      8 # time.sleep(3)
----> 9 ds2 = open_dataset("s3://noaa-ufs-gdas-pds/test_ar.zarr")
     10 ds2

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/__init__.py:34, in open_dataset(*args, **kwargs)
     33 def open_dataset(*args, **kwargs):
---> 34     ds = _open_dataset(*args, **kwargs) #<========================================
     35     ds = ds.mutate()
     36     ds.arguments = {"args": args, "kwargs": kwargs}

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/misc.py:280, in _open_dataset(*args, **kwargs)
    278 for a in args:
    279     print("Accessed _open_dataset") #<============================================ 
--> 280     sets.append(_open(a))
    282 if "xy" in kwargs:
    283     from .xy import xy_factory

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/misc.py:189, in _open(a)
    187 if isinstance(a, str):
    188     print("Accessed _open & arg is str type") # <======================================================
--> 189     return Zarr(zarr_lookup(a)).mutate()
    191 if isinstance(a, PurePath):
    192     print("Accessed _open & arg is a PurePath")

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/stores.py:186, in Zarr.__init__(self, path)
    184 self.was_zarr = False
    185 self.path = str(path)
--> 186 self.z = open_zarr(self.path) 
    187 print(self.path)
    188 print("\n@@@@open_zarr(path):", self.z)

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/stores.py:171, in open_zarr(path, dont_fail, cache)
    168         store = zarr.LRUStoreCache(store, max_size=cache)
    169         print("44")
--> 171     return zarr.convenience.open(store, "r")
    172 except zarr.errors.PathNotFoundError:
    173     if not dont_fail:

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/convenience.py:135, in open(store, mode, zarr_version, path, **kwargs)
    133     return open_array(_store, mode=mode, **kwargs)
    134 elif contains_group(_store, path):
--> 135     return open_group(_store, mode=mode, **kwargs)
    136 else:
    137     raise PathNotFoundError(path)

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/hierarchy.py:1600, in open_group(store, mode, cache_attrs, synchronizer, path, chunk_store, storage_options, zarr_version, meta_array)
   1597 # determine read only status
   1598 read_only = mode == "r"
-> 1600 return Group(
   1601     store,
   1602     read_only=read_only,
   1603     cache_attrs=cache_attrs,
   1604     synchronizer=synchronizer,
   1605     path=path,
   1606     chunk_store=chunk_store,
   1607     zarr_version=zarr_version,
   1608     meta_array=meta_array,
   1609 )

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/hierarchy.py:201, in Group.__init__(self, store, path, read_only, chunk_store, cache_attrs, synchronizer, zarr_version, meta_array)
    199             raise GroupNotFoundError(path) from e
    200 else:
--> 201     self._meta = self._store._metadata_class.decode_group_metadata(meta_bytes)
    203 # setup attributes
    204 if self._version == 2:

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/meta.py:197, in Metadata2.decode_group_metadata(cls, s)
    195 @classmethod
    196 def decode_group_metadata(cls, s: Union[MappingType, bytes, str]) -> MappingType[str, Any]:
--> 197     meta = cls.parse_metadata(s)
    199     # check metadata format version
    200     zarr_format = meta.get("zarr_format", None)

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/meta.py:103, in Metadata2.parse_metadata(cls, s)
     99     meta = s
    101 else:
    102     # assume metadata needs to be parsed as JSON
--> 103     meta = json_loads(s)
    105 return meta

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/util.py:76, in json_loads(s)
     74 def json_loads(s: Union[bytes, str]) -> Dict[str, Any]:
     75     """Read JSON in a consistent way."""
---> 76     return json.loads(ensure_text(s, "utf-8"))

File ~/miniconda3/envs/anemoi_env/lib/python3.11/json/__init__.py:346, in loads(s, cls, object_hook, parse_float, parse_int, parse_constant, object_pairs_hook, **kw)
    341     s = s.decode(detect_encoding(s), 'surrogatepass')
    343 if (cls is None and object_hook is None and
    344         parse_int is None and parse_float is None and
    345         parse_constant is None and object_pairs_hook is None and not kw):
--> 346     return _default_decoder.decode(s)
    347 if cls is None:
    348     cls = JSONDecoder

File ~/miniconda3/envs/anemoi_env/lib/python3.11/json/decoder.py:337, in JSONDecoder.decode(self, s, _w)
    332 def decode(self, s, _w=WHITESPACE.match):
    333     """Return the Python representation of ``s`` (a ``str`` instance
    334     containing a JSON document).
    335 
    336     """
--> 337     obj, end = self.raw_decode(s, idx=_w(s, 0).end())
    338     end = _w(s, end).end()
    339     if end != len(s):

File ~/miniconda3/envs/anemoi_env/lib/python3.11/json/decoder.py:355, in JSONDecoder.raw_decode(self, s, idx)
    353     obj, end = self.scan_once(s, idx)
    354 except StopIteration as err:
--> 355     raise JSONDecodeError("Expecting value", s, err.value) from None
    356 return obj, end

JSONDecodeError: Expecting value: line 1 column 1 (char 0)

5) Test if a zarr in a GS bucket can be converted to anemoi format via the latest anemoi-dataset package AND anemoi-dataset develop branch. Conclusion: With anemoi-dataset latest version, a connection to GCP server cannot be established when using the GS URL & unable to extract metadata and convert to json due to JSONDecodeError: Expecting value: line 1 column 1 (char 0) wen using GCP HTTPS URL. With anemoi-dataset develop branch, 'data' feature in the dataset could not be found.

> With anemoi-datasets create, using GS URL...
** Results:
anemoi_test)     anemoi % anemoi-datasets create test_gcp_zarr.yaml test_gcp_zarr.zarr
2024-09-16 11:54:30 INFO Task init((),{}) starting
2024-09-16 11:54:30 INFO Setting flatten_grid=True in config
2024-09-16 11:54:30 INFO Setting ensemble_dimension=2 in config
2024-09-16 11:54:30 INFO Setting flatten_grid=True in config
2024-09-16 11:54:30 INFO Setting ensemble_dimension=2 in config
2024-09-16 11:54:30 INFO {'start': datetime.datetime(2021, 12, 31, 9, 0), 'end': datetime.datetime(2021, 12, 31, 22, 0), 'frequency': '1h', 'group_by': 'monthly'}
2024-09-16 11:54:30 INFO Groups(dates=1)
2024-09-16 11:54:30 INFO FunctionAction: url=gs://gcp-public-data-arco-era5/ar/1959-2022-1h-360x181_equiangular_with_poles_conservative.zarr param=2m_temperature level=[1000] 
2024-09-16 11:54:30 INFO Minimal input for 'init' step (using only the first date) :
2024-09-16 11:54:30 INFO xarray-zarr(['2021-12-31T09:00:00'])
2024-09-16 11:54:30 INFO Config loaded ok:
2024-09-16 11:54:30 INFO Found 14 datetimes.
2024-09-16 11:54:30 INFO Dates: Found 14 datetimes, in 1 groups: 
2024-09-16 11:54:30 INFO Missing dates: 0
2024-09-16 11:54:33 WARNING Compute Engine Metadata server unavailable on attempt 1 of 3. Reason: timed out
2024-09-16 11:54:37 WARNING Compute Engine Metadata server unavailable on attempt 2 of 3. Reason: timed out
2024-09-16 11:54:39 WARNING Compute Engine Metadata server unavailable on attempt 3 of 3. Reason: [Errno 64] Host is down
2024-09-16 11:54:39 WARNING Authentication failed using Compute Engine authentication due to unavailable metadata server.
2024-09-16 11:54:39 WARNING Compute Engine Metadata server unavailable on attempt 1 of 5. Reason: HTTPConnectionPool(host='metadata.google.internal', port=80): Max retries exceeded with url: /computeMetadata/v1/instance/service-accounts/default/?recursive=true (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x11c4bdf30>: Failed to establish a new connection: [Errno 8] nodename nor servname provided, or not known'))
2024-09-16 11:54:40 WARNING Compute Engine Metadata server unavailable on attempt 2 of 5. Reason: HTTPConnectionPool(host='metadata.google.internal', port=80): Max retries exceeded with url: /computeMetadata/v1/instance/service-accounts/default/?recursive=true (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x11c4be4a0>: Failed to establish a new connection: [Errno 8] nodename nor servname provided, or not known'))
2024-09-16 11:54:42 WARNING Compute Engine Metadata server unavailable on attempt 3 of 5. Reason: HTTPConnectionPool(host='metadata.google.internal', port=80): Max retries exceeded with url: /computeMetadata/v1/instance/service-accounts/default/?recursive=true (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x11c4be8f0>: Failed to establish a new connection: [Errno 8] nodename nor servname provided, or not known'))
2024-09-16 11:54:46 WARNING Compute Engine Metadata server unavailable on attempt 4 of 5. Reason: HTTPConnectionPool(host='metadata.google.internal', port=80): Max retries exceeded with url: /computeMetadata/v1/instance/service-accounts/default/?recursive=true (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x11c4bee00>: Failed to establish a new connection: [Errno 8] nodename nor servname provided, or not known'))

> With anemoi-datasets create, using GCP HTTPS URL...
** Results:

(anemoi_test)     anemoi % anemoi-datasets create test_gcp_zarr.yaml test_gcp_zarr.zarr
2024-09-16 12:08:32 INFO Task init((),{}) starting
2024-09-16 12:08:32 INFO Setting flatten_grid=True in config
2024-09-16 12:08:32 INFO Setting ensemble_dimension=2 in config
2024-09-16 12:08:32 INFO Setting flatten_grid=True in config
2024-09-16 12:08:32 INFO Setting ensemble_dimension=2 in config
2024-09-16 12:08:32 INFO {'start': datetime.datetime(2021, 12, 31, 9, 0), 'end': datetime.datetime(2021, 12, 31, 22, 0), 'frequency': '1h', 'group_by': 'monthly'}
2024-09-16 12:08:32 INFO Groups(dates=1)
2024-09-16 12:08:32 INFO FunctionAction: url=https://console.cloud.google.com/storage/browser/gcp-public-data-arco-era5/ar/1959-2022-1h-360x181_equiangular_with_poles_conservative.zarr param=2m_temperature level=[1000] 
2024-09-16 12:08:32 INFO Minimal input for 'init' step (using only the first date) :
2024-09-16 12:08:32 INFO xarray-zarr(['2021-12-31T09:00:00'])
2024-09-16 12:08:32 INFO Config loaded ok:
2024-09-16 12:08:32 INFO Found 14 datetimes.
2024-09-16 12:08:32 INFO Dates: Found 14 datetimes, in 1 groups: 
2024-09-16 12:08:32 INFO Missing dates: 0
2024-09-16 12:08:33 ERROR Error in execute
Traceback (most recent call last):
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 586, in datasource
    return _tidy(self.action.function(FunctionContext(self), self.dates, *args, **kwargs))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray_zarr.py", line 15, in execute
    return load_many("🇿", context, dates, url, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray/__init__.py", line 77, in load_many
    result.append(load_one(emoji, context, dates, path, **kwargs))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray/__init__.py", line 47, in load_one
    data = xr.open_zarr(name_to_zarr_store(dataset), **options)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1103, in open_zarr
    ds = open_dataset(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/api.py", line 611, in open_dataset
    backend_ds = backend.open_dataset(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1173, in open_dataset
    store = ZarrStore.open_group(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 483, in open_group
    zarr_group, consolidate_on_close, close_store_on_close = _get_open_params(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1335, in _get_open_params
    zarr_group = zarr.open_consolidated(store, **open_kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/convenience.py", line 1360, in open_consolidated
    meta_store = ConsolidatedStoreClass(store, metadata_key=metadata_key)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/storage.py", line 3046, in __init__
    meta = json_loads(self.store[metadata_key])
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/util.py", line 76, in json_loads
    return json.loads(ensure_text(s, "utf-8"))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/__init__.py", line 346, in loads
    return _default_decoder.decode(s)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/decoder.py", line 337, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/decoder.py", line 355, in raw_decode
    raise JSONDecodeError("Expecting value", s, err.value) from None
json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)
Traceback (most recent call last):
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/utils/cli.py", line 135, in cli_main
    cmd.run(args)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 64, in run
    self.serial_create(args)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 74, in serial_create
    task("init", options)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/commands/create.py", line 29, in task
    result = c.run()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/__init__.py", line 355, in run
    return self._run()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/__init__.py", line 375, in _run
    variables = self.minimal_input.variables
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 480, in variables
    self.build_coords()
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 431, in build_coords
    from_data = self.get_cube().user_coords
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 226, in get_cube
    ds = self.datasource
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/functools.py", line 981, in __get__
    val = self.func(instance)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 90, in wrapper
    result = method(self, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/template.py", line 26, in wrapper
    result = method(self, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/trace.py", line 56, in wrapper
    result = method(self, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/input.py", line 586, in datasource
    return _tidy(self.action.function(FunctionContext(self), self.dates, *args, **kwargs))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray_zarr.py", line 15, in execute
    return load_many("🇿", context, dates, url, *args, **kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray/__init__.py", line 77, in load_many
    result.append(load_one(emoji, context, dates, path, **kwargs))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/anemoi/datasets/create/functions/sources/xarray/__init__.py", line 47, in load_one
    data = xr.open_zarr(name_to_zarr_store(dataset), **options)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1103, in open_zarr
    ds = open_dataset(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/api.py", line 611, in open_dataset
    backend_ds = backend.open_dataset(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1173, in open_dataset
    store = ZarrStore.open_group(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 483, in open_group
    zarr_group, consolidate_on_close, close_store_on_close = _get_open_params(
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/xarray/backends/zarr.py", line 1335, in _get_open_params
    zarr_group = zarr.open_consolidated(store, **open_kwargs)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/convenience.py", line 1360, in open_consolidated
    meta_store = ConsolidatedStoreClass(store, metadata_key=metadata_key)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/storage.py", line 3046, in __init__
    meta = json_loads(self.store[metadata_key])
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/site-packages/zarr/util.py", line 76, in json_loads
    return json.loads(ensure_text(s, "utf-8"))
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/__init__.py", line 346, in loads
    return _default_decoder.decode(s)
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/decoder.py", line 337, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "  /miniconda3/envs/anemoi_test/lib/python3.10/json/decoder.py", line 355, in raw_decode
    raise JSONDecodeError("Expecting value", s, err.value) from None
json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)
2024-09-16 12:08:33 ERROR 
💣 Expecting value: line 1 column 1 (char 0)
2024-09-16 12:08:33 ERROR 💣 Exiting

> With anemoi-datasets develop branch
- from __init__ import add_dataset_path
- from __init__ import open_dataset
- ds2 = open_dataset("gs://gcp-public-data-arco-era5/ar/1959-2022-1h-360x181_equiangular_with_poles_conservative.zarr")

- ** Result: ** 
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/hierarchy.py:538, in Group.__getattr__(self, item)
    537 try:
--> 538     return self.__getitem__(item)
    539 except KeyError as e:

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/hierarchy.py:511, in Group.__getitem__(self, item)
    510 else:
--> 511     raise KeyError(item)

KeyError: 'data'

The above exception was the direct cause of the following exception:

AttributeError                            Traceback (most recent call last)
Cell In[7], line 9
      3 from __init__ import open_dataset
      5 #add_dataset_path("https://object-store.os-api.cci1.ecmwf.int/ml-examples/")
      6 
      7 # import time
      8 # time.sleep(3)
----> 9 ds2 = open_dataset("gs://gcp-public-data-arco-era5/ar/1959-2022-1h-360x181_equiangular_with_poles_conservative.zarr")
     10 ds2

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/__init__.py:34, in open_dataset(*args, **kwargs)
     33 def open_dataset(*args, **kwargs):
---> 34     ds = _open_dataset(*args, **kwargs) #<========================================
     35     ds = ds.mutate()
     36     ds.arguments = {"args": args, "kwargs": kwargs}

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/misc.py:280, in _open_dataset(*args, **kwargs)
    278 for a in args:
    279     print("Accessed _open_dataset") #<============================================ 
--> 280     sets.append(_open(a))
    282 if "xy" in kwargs:
    283     from .xy import xy_factory

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/misc.py:189, in _open(a)
    187 if isinstance(a, str):
    188     print("Accessed _open & arg is str type") # <======================================================
--> 189     return Zarr(zarr_lookup(a)).mutate()
    191 if isinstance(a, PurePath):
    192     print("Accessed _open & arg is a PurePath")

File ~ /anemoi/gh_most_uptodate/troubleshooting/anemoi-datasets/src/anemoi/datasets/data/stores.py:192, in Zarr.__init__(self, path)
    189     print("ATTRIB:", [i for i in self.z.attrs])
    191 # This seems to speed up the reading of the data a lot
--> 192 self.data = self.z.data
    193 self.missing = set()

File ~/miniconda3/envs/anemoi_env/lib/python3.11/site-packages/zarr/hierarchy.py:540, in Group.__getattr__(self, item)
    538     return self.__getitem__(item)
    539 except KeyError as e:
--> 540     raise AttributeError from e

AttributeError: 