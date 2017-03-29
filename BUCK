windows_sources = glob([
  'src/win32/**/*.cpp',
])

platform_sources = windows_sources

cxx_library(
  name = 'libnoise',
  header_namespace = 'noise',
  exported_headers = subdir_glob([
    ('src', 'model/*.h'),
    ('src', 'module/*.h'),
    ('src', '*.h'),
  ]),
  srcs = glob([
    'src/**/*.cpp',
  ],
  excludes = platform_sources),
  platform_srcs = [
    ('^windows.*', windows_sources),
  ],
  visibility = [
    'PUBLIC',
  ],
)
