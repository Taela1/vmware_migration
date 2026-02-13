# Metadata file structure

## Alignment between metadata file and disk file

The name of the disk file will be based on the name of the metadata file itself. Example: 
Given "vltestt001.at.inside.json" as metdadata file the expected disk file needs to be named "vlttestt001.at.inside.qcow2" and be readable within the same source as the metadata file.

## Description and examples

### org_id
The Exoscale organization this VM should be imported to. Provided as Exoscale UUID.
Example of an org_id: ae0ba860-e935-4b89-9847-06705d3f4c74

The org_id is unique and mandatory.
Type: UUID

### name
The name of the VM. This name is used to display the VM, if cloud-init is configured this hostname will be set on start up.

The name is unique and mandatory
Type: string

### zone
The name of the zone the VM should be imported to.
Available zones:
┼──────────┼
│   NAME   │
┼──────────┼
│ at-vie-1 │
│ at-vie-2 │
│ bg-sof-1 │
│ ch-dk-2  │
│ ch-gva-2 │
│ de-fra-1 │
│ de-muc-1 │
│ hr-zag-1 │
┼──────────┼

The zone is unique and mandatory.
Type: string

### deploy_target
The UUID of the environment the VM should be provisioned in. Blank is not allowed as we need to provision on the specialized hypervisor farm.

The deploy_target is unique and mandatory.
Type: UUID

### service_offering
The UUID of the service offering (t-shirt) for the VM.
Available offerings:
┼──────────────────────────────────────┼───────────────┼─────────────┼
│                  ID                  │    FAMILY     │    SIZE     │
┼──────────────────────────────────────┼───────────────┼─────────────┼
│ 71004023-bb72-4a97-b1e9-bc66dfce9470 │ standard      │ micro       │
│ b6cd1ff5-3a2f-4e9d-a4d1-8988c1191fe8 │ standard      │ tiny        │
│ 21624abb-764e-4def-81d7-9fc54b5957fb │ standard      │ small       │
│ b6e9d1e8-89fc-4db3-aaa4-9b4c5b1d0844 │ standard      │ medium      │
│ c6f99499-7f59-4138-9427-a09db13af2bc │ standard      │ large       │
│ 350dc5ea-fe6d-42ba-b6c0-efb8b75617ad │ standard      │ extra-large │
│ a216b0d1-370f-4e21-a0eb-3dfc6302b564 │ standard      │ huge        │
│ c0d3fb5d-6fdb-4a63-9361-3e5cfa8b36d0 │ standard      │ mega        │
│ 74bfaf4e-7d67-4adf-9322-12b9a36e84f7 │ standard      │ titan       │
│ 011a5079-845d-467b-a660-8685dad1cb67 │ standard      │ jumbo       │
│ 221d39c3-b2b9-4014-b32b-5d262f684eff │ cpu           │ extra-large │
│ 68c91810-55ed-4685-9771-00d9adf7b7c0 │ cpu           │ huge        │
│ c2f204df-29fc-4c20-b5c4-bdb21282cecc │ cpu           │ mega        │
│ e1ae0088-27fd-4185-a057-075ea0b0aa02 │ cpu           │ titan       │
│ dd6abc94-337f-4732-baff-ed745f8bd4f5 │ memory        │ extra-large │
│ efbf55db-01c9-4c73-973f-cecc4d26dcde │ memory        │ huge        │
│ 306eeeae-38e9-4add-897b-4eff0b019a6d │ memory        │ mega        │
│ 68a4780f-cc91-4df6-a735-d679318289bc │ memory        │ titan       │
│ 8a52e80d-b1d0-4efb-8059-a931fa33c5a1 │ standard      │ colossus    │
│ ea24461a-41e8-49f1-a22a-0f00e3507604 │ cpu           │ titan48c    │
│ 68dec7c8-7ae8-43b6-ad4a-d508152110fe │ cpu           │ colossus    │
┼──────────────────────────────────────┼───────────────┼─────────────┼

The service_offering is unique and mandatory.
Type: UUID

### disk_size
Disk size in GiB to be used for the VM. Provided as number without 

The disk_size is unique and mandatory.
Type: int

### template_id
UUID of the template to use as basis for the VM. Can be a standard Exoscale template or a custom template used as placeholder.
Available standard templates:
┼──────────────────────────────────────┼─────────────────────────────────────────────────────┼─────────────────────────┼───────────────────────────────┼
│                  ID                  │                        NAME                         │         FAMILY          │         CREATION DATE         │
┼──────────────────────────────────────┼─────────────────────────────────────────────────────┼─────────────────────────┼───────────────────────────────┼
│ 14ba535f-1bf6-4da6-92b2-e15bcf8166f5 │ Airlock WAF 7.1                                     │ airlock waf             │ 2021-02-20 23:40:07 +0000 UTC │
│ 2d77c172-3eb5-4227-9de5-b687b6f12f39 │ Linux Arch Rolling                                  │ arch                    │ 2026-01-27 23:25:22 +0000 UTC │
│ 618cc381-ecfb-425f-9aa7-a32b8b915bcc │ Linux CentOS Stream 10 64-bit                       │ centos stream           │ 2026-01-27 22:28:52 +0000 UTC │
│ 92560ced-53ba-49bb-be45-3f9eb142cc51 │ Linux CentOS Stream 9 64-bit                        │ centos stream           │ 2026-01-27 10:46:20 +0000 UTC │
│ 090f3c9f-a50f-4f53-a056-4421abe1d396 │ CheckPoint R80.40 BYOL                              │ checkpoint byol         │ 2021-05-21 16:49:56 +0000 UTC │
│ d21cddc1-b6d2-47ac-be63-d8a8a2adeba1 │ Cisco ASAv 9.16.3 BYOL                              │ cisco asav byol         │ 2022-10-17 09:31:12 +0000 UTC │
│ 8b48f0ac-52ea-414d-b042-52677d49e968 │ Linux Debian 12 (Bookworm) 64-bit                   │ debian                  │ 2026-01-29 11:03:50 +0000 UTC │
│ 8c54abea-0176-4c2b-a9b4-83d4b9975733 │ Linux Debian 13 (Trixie) 64-bit                     │ debian                  │ 2026-01-27 23:06:36 +0000 UTC │
│ 528ef30b-169f-4689-af69-22804fdd1f69 │ F5 Distributed Cloud Services v9.2023.29 BYOL       │ f5 byol                 │ 2024-01-23 12:12:00 +0000 UTC │
│ 07ef8595-4fd8-4a36-b4cc-02c863553dd0 │ Linux Fedora CoreOS 42 64-bit                       │ fedora coreos           │ 2025-12-04 08:42:25 +0000 UTC │
│ 9821595e-dfdc-4645-8340-8dbcfd0f4890 │ Linux Fedora CoreOS 43 64-bit                       │ fedora coreos           │ 2026-01-30 08:37:09 +0000 UTC │
│ 05d26b40-0b5c-448a-9f7c-a24a6837adb1 │ Exoscale Flexible Storage 12                        │ flexible storage        │ 2026-01-15 09:34:16 +0000 UTC │
│ 65236ea2-7b74-48cd-a0f7-132126549eec │ FortiGate 7.4.8 BYOL                                │ fortigate byol          │ 2025-09-09 09:11:15 +0000 UTC │
│ c111f20e-ebdf-405e-b53e-ee1a39be897a │ FortiGate 7.6.2 BYOL                                │ fortigate byol          │ 2025-02-18 09:26:17 +0000 UTC │
│ 474e46f9-53b6-4ffd-91c2-a89266bfb6af │ Icinga2 Master (Rocky 9) - BYOL                     │ icingabyol              │ 2025-01-29 16:11:53 +0000 UTC │
│ d740e970-bd36-4307-b901-d5fe54c7afdb │ IPFire 2.29 - Core Update 197                       │ ipfire                  │ 2025-09-23 15:18:38 +0000 UTC │
│ bf54df8b-4f64-46d6-9ca6-95b03fc020c1 │ OpenBSD 7.8 64-bit                                  │ openbsd                 │ 2025-10-30 17:30:16 +0000 UTC │
│ e2525196-b97f-4d1a-bca9-61dff773af8a │ OpenBSD 7.7 64-bit                                  │ openbsd                 │ 2025-05-05 07:04:17 +0000 UTC │
│ f934a7ed-eb4e-417d-b087-0617e9c13b66 │ OpenSUSE Leap 16.0 64-bit                           │ opensuse                │ 2025-12-02 11:17:59 +0000 UTC │
│ 987d015d-3d12-4fa2-8ca4-e174c4c17433 │ Palo Alto Network FW - 10.2.1                       │ palo alto               │ 2022-09-05 12:56:24 +0000 UTC │
│ 64a6cd8d-6b33-4545-8792-3435b5196717 │ Linux RedHat 10.1 BYOL 64-bit                       │ redhat byol             │ 2025-12-15 10:08:51 +0000 UTC │
│ da19e989-af88-4c26-b14a-da9124eb151d │ Linux RedHat 9.7 BYOL 64-bit                        │ redhat byol             │ 2025-12-15 10:20:24 +0000 UTC │
│ 374db637-3aa1-47a1-97ff-8bf9ef6702fc │ Linux RedHat 8.10 BYOL 64-bit                       │ redhat byol             │ 2025-10-30 08:56:01 +0000 UTC │
│ ff26c9c6-8091-4c37-b994-5c6d6192ac5c │ Rocky Linux 10 64-bit                               │ rocky linux             │ 2026-01-27 14:20:56 +0000 UTC │
│ 0f56a80d-b109-4c73-afbd-fbc48a6f79ba │ Rocky Linux 9 (Blue Onyx) 64-bit                    │ rocky linux             │ 2026-01-30 08:41:22 +0000 UTC │
│ 54f1ec9b-81a0-45bf-b86b-73bbee65e52b │ SUSE Linux Enterprise Server 15 SP7 - 20251218-1621 │ sles                    │ 2026-01-08 11:09:14 +0000 UTC │
│ 188e6dc9-7b29-4db4-a8af-fc6368660738 │ Linux Ubuntu 24.04 LTS 64-bit                       │ ubuntu                  │ 2026-01-29 11:03:34 +0000 UTC │
│ 8e3afcbf-b8dd-40f3-9ee8-4f994586238c │ Linux Ubuntu 25.10 64-bit                           │ ubuntu                  │ 2026-01-29 11:05:34 +0000 UTC │
│ c231ff61-20ca-4742-94e7-4fafe44b7b61 │ Linux Ubuntu 22.04 LTS 64-bit                       │ ubuntu                  │ 2026-01-29 11:07:56 +0000 UTC │
│ 9f882dd6-50e3-405a-baec-b9f19071e762 │ Linux Ubuntu 25.04 64-bit                           │ ubuntu                  │ 2026-01-30 07:28:50 +0000 UTC │
│ b3bafc66-ffd5-47a1-910b-a810c8aa13cf │ VMware SD-WAN 3.3.2 BYOL                            │ vmware sd-wan           │ 2020-10-16 08:38:56 +0000 UTC │
│ 9f3ff9c1-1bbd-4f60-afaa-3e8d2f266bed │ VyOS 1.4.4                                          │ vyos                    │ 2026-01-05 12:29:38 +0000 UTC │
│ c20ad5c6-1de9-4c42-8b96-f9477c82c646 │ Windows Server 2025                                 │ windows                 │ 2026-01-15 14:27:22 +0000 UTC │
│ 80b71d54-433c-4fac-aca7-68c7d35af1ea │ Windows Server 2022                                 │ windows                 │ 2026-01-15 14:23:55 +0000 UTC │
│ f374fabb-5751-4239-9010-ebbe59ea008c │ Windows Server 2022 with SQL 2022                   │ windows server with sql │ 2026-01-15 14:27:01 +0000 UTC │
│ 924de7f6-3f0a-4ade-9f72-6d9f180c4279 │ Windows Server 2025 with SQL 2022                   │ windows server with sql │ 2026-01-15 14:26:00 +0000 UTC │
┼──────────────────────────────────────┼─────────────────────────────────────────────────────┼─────────────────────────┼───────────────────────────────┼

The template_id is unique and mandatory.
Type: UUID

### ip_assignment
ipv4: First NIC will be attached to Exoscale network infrastructure and will receive a public IPv4 IP out of Exoscales pool via DHCP
ipv6: First NIC will be attached to Exoscale network infrastructure and will receive a public IPv4 and IPv6 IP out of Exoscales pool via DHCP
private: All NICs will be attached to Exoscale private networks configured. If no private networks configured VM will be deployed without NIC.

The ip_assignment is unique and mandatory.
Type: string

### vtpm
Set to true if vTPM should be attached to the VM. Set to false if vTPM is not required.

The vtpm is unique and mandatory.
Type: boolean

### secureboot
Set to true if secureboot should be attached to the VM. Set to false if secureboot is not required.

The secureboot is unique and mandatory.
Type: boolean

### uefi
Set to true if system is UEFI, set to false if system is BIOS/Legacy

The uefi is unique and mandatory.
Type: boolean

### vss
Set to true if system should use VSS as snapshot technology, set to false if VSS technology should not be used.

The vss is unique and mandatory.
Type: boolean

### labels
Enter one or multiple key-values as labels

The labels are not mandatory and not unique.
Type: key-value

### private_networks
Enter none or multiple UUIDs of private networks the VM should be attached to.

The private_networks are not mandatory and not unique
Type: UUID

### security_groups
Enter none or multiple UUIDs of security groups the VM should be attached to. Only necceary if "ip_assignment" is no private.

The security_groups are not mandatory and not unique.
Type: UUID
