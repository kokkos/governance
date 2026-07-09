# Kokkos sub-projects and life-cycle

The Kokkos project is part of the High Performance Software Foundation (HPSF).
As such and as every project in HPSF, Kokkos is assigned a stage in the HPSF life-cycle mode.
As of now (2026-06-03), Kokkos is at the "core" level in this life-cycle.

But the Kokkos project is also itself made of a set of sub-projects.
Each sub-project is assigned a stage in the Kokkos life-cycle.
This document defines and describes the various life-cycle stages in Kokkos.

The Kokkos life-cycle stages are the following:
* Experimental seed
* Young sprout
* Maturing
* Sustained
* Retired

The life-cycle stage is assigned by the Kokkos project leads after discussion by the sub-project leads.

## Kokkos sub-projects

The sub-projects in Kokkos are:

| Subproject | Lifecycle | Category |
| --- | --- | --- |
| Core | Sustained | Base |
| Kernels | Sustained | Base |
| Tools | Maturing | Base |
| Tutorials | Maturing | Outreach |
| kokkos.org | Maturing | Outreach |
| mdspan | Maturing | Base |
| FFT | Maturing | Auxiliary |
| Comm | Young Sprout | Auxiliary |
| pyKokkos | Young Sprout | Auxiliary |
| Fortran-Interop | Young Sprout | Auxiliary |
| Resilience | Young Sprout | Auxiliary |
| stdBLAS | Young Sprout | Auxiliary |

## Kokkos Life-cycle

### Experimental seed

* Has a well identified maintainer
* Is in github kokkos organization
* Has a licencing scheme acceptable for the ecosystem
* Tries their best to follow the Kokkos common design guidelines
* Might remain at this stage of the life-cycle or switch to Young sprout at some point

### Young sprout

* Fulfills all criteria of the Experimental seed stage
* Has at least one production application that plans to rely on this project
* Plans to grow to the Maturing level and then Sustainable at some point


### Maturing

* Fulfills all criteria of the Young Sprout stage & is actively maintained
* Has setup processes to welcome external developers as described in HPSF established life-cycle stage
* Has defined releases and tries to follow Kokkos synchronized release scheme
* Has made a commitment on API stability, similar to what’s required for 1.0 semver
* Has set up some CI
	- For dependencies from the Kokkos ecosystem, both releases & latest dev. branch are tested
	- Has a maintained publicly accessible documentation
* Required dependencies should be Maturing+ or good argument should be provided to show that the subset used is at that maturity level
* Favors dependencies from the Kokkos ecosystem
* Leverages Kokkos infra for communication (slack, website, etc.)

### Sustained

* Fulfills all criteria of the Maturing stage
* Implements Kokkos synchronized release scheme
* Is used in production by applications from at least 2 distinct Kokkos stakeholders
* Required dependencies are all Sustainable or good argument should be provided to show that the subset used is at that maturity level
* Follows the Kokkos common design guidelines
* Has spent at least 6 month at the Mature stage
* Supports (including CI) all Kokkos common supported platforms

### Retired

* Has no active maintainer anymore
* Makes no commitment at all

## orthogonal classification

Projects will be classified in one of these categories by their maintainer, after validation by Kokkos leadership

* Kokkos base libraries & tools
	- Programming model
	- Base math
	- Tooling for this level
* Kokkos auxiliary libraries & tools
* Kokkos outreach and training efforts

## Kokkos common design guidelines

Projects define together some common design guidelines that are validated by Kokkos leads

* Namespace nomenclature must be
	- Features in the experimental:: namespace follow the rules of the Experimental stage (no commitment regarding deprecation, can be changed/removed without warning at any time)
	- Features in the impl:: namespace are implementation details and no user should access them, no commitment is made at all about those
	- The name of a project (with any case) is reserved as a (root) namespace for that project, it must not be used 
		* No other (root) namespace containing the word “kokkos” should be used
	- All other namespaces must follow normal deprecation / removal rules
* Spack packages must be provided

## Kokkos common supported platforms

Projects define together the common supported platforms that are validated by Kokkos leadership

* Linux x86 with GCC 10.4+ / clang 14+ / Intel 2022.0+
* Nvidia GPUs Volta+ with Cuda 11.8+ & clang 15+ / nvcc 12.2+ / nvc++ 22.3+
* AMD GPUs MI200X+ with Rocm 6.2+ & Clang 15+ / hipcc 6.2+
* Linux ARM CPUs with GCC 10.4+ / clang 14+

Not necessary, but nice to have:
* Windows x86 with MSVC 19.30+
* Intel GPUs ???+ with ??? & Intel 2024.2.1+

## Kokkos synchronized release scheme

Projects define together a synchronized release scheme that is validated by Kokkos leadership

* Projects must follow semantic versioning
* minor & major releases must be synchronized (same version number)
	- Project leaders will agree on a predictable schedule for minor & major releases
		* (Typically for now, 3 years for major, 4 month for minor)
