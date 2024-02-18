# `bak`

Create and restore simple file/directory backups

## Installation

`bak` is a simple bash script. Put it anywhere on your path and ensure it has executable permissions.

## Usage

`bak` will copy a local file/directory with a timestamped suffix:

    % ls -l
    ls -l
    total 0
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 bc
    % bak a
    % ls -l
    total 0
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a.240217-225351.bak
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 bc

Running `bak` on a `bak`-generated backup file will restore that backup to the original filename. If the original filename already exists, it will first be `bak`ed up.

    % bak a.240217-225351.bak
    % ls -l
    total 0
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a.240217-225521.bak
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 bc

Because `bak` uses timestamp suffixes, you can create several local backups. `bak` is simple and only timestamps to the second, which should be more than sufficient for its intended usage.

    % bak a
    % bak a
    total 0
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 a.240217-225521.bak
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:58 a.240217-225813.bak
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:58 a.240217-225815.bak
    -rw-r--r--  1 drootang  staff     0B Feb 17 22:53 bc
