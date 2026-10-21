# perl-matrix

A reusable GitHub Actions workflow that tests a Perl distribution the way
CPAN smokers do: `cpanm --installdeps .`, then
`perl Makefile.PL && make && make test`.

It covers the environments that show up on CPAN Testers: Linux across old
and modern perls (5.10 through 5.44), FreeBSD and Solaris with their stock
perls, and Cygwin.

## Use

In your repository's workflow:

```yaml
jobs:
  environments:
    uses: nicomen/perl-matrix/.github/workflows/perl-matrix.yml@main
```

## Inputs

All optional:

| Input | Default | Meaning |
|-------|---------|---------|
| `perl-versions` | `5.10` … `5.44` | JSON array for the Linux matrix |
| `freebsd-releases` | `["14.3","15.0"]` | FreeBSD releases; `[]` disables the job |
| `extra-modules` | none | Extra CPAN modules to install beyond declared deps |
| `cygwin` | `true` | Run the Cygwin job |
| `solaris` | `true` | Run the Solaris job |

```yaml
jobs:
  environments:
    uses: nicomen/perl-matrix/.github/workflows/perl-matrix.yml@main
    with:
      extra-modules: Moo
      solaris: false
```
