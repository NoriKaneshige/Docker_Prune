# Docker_Prune
## Basically clean everything of engine that is not actively being used in running container 
[Docker_Prune_Bret_Fisher_Youtube](https://www.youtube.com/watch?v=_4QzP7uwtvI&feature=youtu.be)

### docker system
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system

Usage:	docker system COMMAND

Manage Docker

Commands:
  df          Show docker disk usage
  events      Get real time events from the server
  info        Display system-wide information
  prune       Remove unused data

Run 'docker system COMMAND --help' for more information on a command.
```
### docker system df
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              10                  2                   936.5MB             809.7MB (86%)
Containers          4                   0                   0B                  0B
Local Volumes       37                  0                   2.428GB             2.428GB (100%)
Build Cache         0                   0                   0B                  0B
```
### docker system image prune
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker image prune
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] y
Total reclaimed space: 0B
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              10                  2                   936.5MB             809.7MB (86%)
Containers          4                   0                   0B                  0B
Local Volumes       37                  0                   2.428GB             2.428GB (100%)
Build Cache         0                   0                   0B                  0B
```
### docker system container prune
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
e1ccc84f983e4d962279c4e563bfd89bbc61df1d00c21086c6906127179035b8
b55f9636900792fb852d7138b12ede402d0b9787f05387fdc7c01da512d82e7a
2d1404040941ff597328a447c0baa6d4b9a0b67978bbecdc469a0af66f950022
6a1189201ac17bc39de61f0aa1c2326f83f613d11b757d46800fb909ea409095

Total reclaimed space: 0B
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              10                  0                   936.5MB             936.5MB (100%)
Containers          0                   0                   0B                  0B
Local Volumes       37                  0                   2.428GB             2.428GB (100%)
Build Cache         0                   0                   0B                  0B
```
### docker system prune --help
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system prune --help

Usage:	docker system prune [OPTIONS]

Remove unused data

Options:
  -a, --all             Remove all unused images not just dangling ones
      --filter filter   Provide filter values (e.g. 'label=<key>=<value>')
  -f, --force           Do not prompt for confirmation
      --volumes         Prune volumes
```

### docker system prune -a
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system prune -a
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all images without at least one container associated to them
  - all build cache

Are you sure you want to continue? [y/N] y
Deleted Images:
untagged: customnginx:latest
deleted: sha256:b71c8c8047778cdc710a1499589d500440b7ab10e1062edd8ac55217c8ac6872
deleted: sha256:2c1855d83b0493a5f421993dd82953685c866bfb970610efbd3bbed68bbc2f8d
deleted: sha256:cd39d820a9f9084ef12d8629ff870c15d66930b20cdd508b83abe16f9f47e7db
deleted: sha256:73bc05f84e67cf5cf1f8d4383fc3f1e96280b23f5f6ca06268f27ee91cda8032
deleted: sha256:61b31d825a226a472ad4a33d773232a0757657eda4c30a2eb5ab92530eaa541e
deleted: sha256:cbfe5bf1c1ffbc7471c17a52ca5c4fe11bf881a30f679d82fbfc74ea441c3a82
deleted: sha256:19be3e10f2c30a82753bc5d91ed7bd43b722e61c08f4744f520ace2839b12090
deleted: sha256:cf9a9e06cc6097b0a1fe2e93c648ff618c85c90bf6f2dd2b2b261a983c93c5be
untagged: nginx-with-html:latest
untagged: norinori400/nginx-with-html:latest
untagged: norinori400/nginx-with-html@sha256:fbe0a3d50d6df8664f21b59c98c8a6c55a42056653dd1217be24f64856c7cb7c
deleted: sha256:31df27b07b7126175e00eaaa4b5a70bd704b5d3739543c78d5ce54a308f67af1
deleted: sha256:a4afbb8419c9dd1222abe322410e3c09804f55ab9a6aeb52ee4524e9fc5b9814
deleted: sha256:e7859fc8ce64f3cb4f52a4ef87c6ff7a4e7dd8438ac3542843079a289de5fa44
untagged: norinori400/norikaneshige/nginx:latest
deleted: sha256:602e111c06b6934013578ad80554a074049c59441d9bcd963cb4a7feccede7a5
deleted: sha256:81eaddad75aaa517b4a597912da28c2f5b905f6e9789dce3aea874b040aad201
deleted: sha256:73cafa8418003ecfaa02360f181c132b2cf4b61433e1bd5c84012941105865c8
deleted: sha256:c2adabaecedbda0af72b153c6499a0555f3a769d52370469d8f6bd6328af9b13
untagged: node:6-alpine
untagged: node@sha256:17258206fc9256633c7100006b1cfdf25b129b6a40b8e5d37c175026482c84e3
untagged: mysql/mysql-server:latest
untagged: mysql/mysql-server@sha256:a82ff720911b2fd40a425fd7141f75d7c68fb9815ec3e5a5a881a8eb49677087
deleted: sha256:716286be47c6246fc8a1e0ce8435aa50485b79521bf7d14f749b616093fd6099
deleted: sha256:5fa0471a4b76785f9a8065a71782e446388ec589901c2efc0c225115d0b6f88d
deleted: sha256:253bfe2a11f0c526bdb61066a2090d3b2e1583fa4c97735c3ebd8fea1359f8d6
deleted: sha256:c2b529bcfb0597e95759e7fca60c83d2a226a8f343b7534f7c9b9979c931e313
deleted: sha256:bc198e3a2f790a31fe27662f4d70f3d5f952428be2e526642452412ad10d879c
untagged: debian:stretch-slim
untagged: debian@sha256:b385ea429b383b690c955043d79050d1cb76346fbca67e3ed3649d5019dd6749
deleted: sha256:fa41698012c736bdf65c3860442f83f790f2b3758747a2e3adafdcb7de691de5
deleted: sha256:83b43189420d069cbdc1421b94c396c6b74d1ad8150933d411a223b145b981ab
untagged: nginx:latest
untagged: nginx@sha256:30dfa439718a17baafefadf16c5e7c9d0a1cde97b4fd84f63b69e13513be7097
untagged: nginx@sha256:f938e7389670418efee4d5a8748600d9ec705170957774d25d4ec73bdbe004e2
untagged: norinori400/nginx:latest
untagged: norinori400/nginx:testing
untagged: norinori400/nginx@sha256:8269a7352a7dad1f8b3dc83284f195bac72027dd50279422d363d49311ab7d9b
deleted: sha256:9beeba249f3ee158d3e495a6ac25c5667ae2de8a43ac2a8bfd2bf687a58c06c9
deleted: sha256:8fb6373b4cca3383756d7fd7843dd92f95827e5f2913609e09a9621dcddb3752
deleted: sha256:8b09841626797a03a9fe5e73aa38aeacf9ff0ce85a3004236ff35234eec3b35c
untagged: testnode:latest
untagged: norinori400/testing-node:latest
untagged: norinori400/testing-node@sha256:0781b843fc0aef3b449faa8aefbbe770acf677b7d838f4363490b590029e1e61
deleted: sha256:6db78297cc20f689cf029e837b960af1c1be161ec4afefca81ca0d4c162c8161
deleted: sha256:87b1cc0fa2214289db1c8aa208bb8033f24ee33d5f31dac18dc0bd2c8e8c6555
deleted: sha256:3bdf46aaeedc5ef7208556b2546ad90651de8e30c69a7b2e5d8ebed83e2fe1e9
deleted: sha256:f1a02e55b2fc4f003117c34850802bc408e3caac5329575fe3a20e7ecafd7fda
deleted: sha256:c376957abac934e82aeac2cafe5d338295405c5cb8434cc2dcef54bd85266096
deleted: sha256:c1e5a373012d237a2696833431096c4cdb3da0aca9636d6dad86627c04389c4a
deleted: sha256:ee9620cbef4d53184c7d23b5e94c520862afb8133fd12b9f2db4ddd996913117
deleted: sha256:9929b57847d55587cb0d10298d5e9807c638cb04505bd400ebee9fb6720ccb09
deleted: sha256:88aa250fdab05f38301de36dfda034faefe2b4798f08052c9478c69a39b39e79
deleted: sha256:76a16d45d774290c5a5e6f5621188c5afa5575e6f7c20ae8b4d416993baa1363
deleted: sha256:1d96c808dbeff5b6a665948e20ba2fe71bcc21acc8ea6b0c2f7dd1d585ee2d8d
deleted: sha256:00a00642ce86a7917fec630b868ee565d2bc327cfc0ae2b29f62b6d5ad99090b
deleted: sha256:2ba10fc433c526837c3ac998b7bd14bdd7e17b391d2c2de5eeb1dfaf620c775f
deleted: sha256:dfc29bfa7d41dd1616257cfe7cb4462c8fd566e9c4d2b2cefb5ea2adf57ad6b8
deleted: sha256:0be2041e37cfef0c9c998468525d13e6516d1cc6fddb81c695cdeb171e663213
deleted: sha256:7b545333d499d38c531833dba772056d5a3e7e251fa748deab0c71bd1cbcb6e7
deleted: sha256:a464c54f93a9e88fc1d33df1e0e39cca427d60145a360962e8f19a1dbf900da9
untagged: nginx:1.17.10-alpine
untagged: nginx@sha256:763e7f0188e378fef0c761854552c70bbd817555dc4de029681a2e972e25e30e
deleted: sha256:89ec9da682137d6b18ab8244ca263b6771067f251562f884c7510c8f1e5ac910
deleted: sha256:2d4747dc369095d2106384421de7e79992c14e3031080b93a436b5ad6e359770
deleted: sha256:3e207b409db364b595ba862cdc12be96dcdad8e36c59a03b7b3b61c946a5741a
untagged: nginx:stable-perl
untagged: nginx@sha256:2bf089718a2fe4e6255742a5924dd6553fdca33ab824d0aa3ef89eee49faa676
deleted: sha256:cf56628552802d2b3c6c2d72f9f58c75126ce2c04ea7cfce8f6f65aba33fc2de
deleted: sha256:28b9c0736131ac3f478ff2253a6f46b830aa8c00898753a6cd582c3832fa7555
deleted: sha256:dd0e0a9958000d29f897d32a9ceaea4e3680d0d34f801a87e9981573ac7efd3c
deleted: sha256:c6bd546053d9adce49b5246d87f84ad7baec09655a65e0cc27f65b423e467f1a
deleted: sha256:ffc9b21953f4cd7956cdf532a5db04ff0a2daa7475ad796f1bad58cfbaf77a07

Total reclaimed space: 936.5MB


Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              0                   0                   0B                  0B
Containers          0                   0                   0B                  0B
Local Volumes       37                  0                   2.428GB             2.428GB (100%)
Build Cache         0                   0                   0B                  0B
```
### docker system prune --volumes
```
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system prune --volumes
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all volumes not used by at least one container
  - all dangling images
  - all dangling build cache

Are you sure you want to continue? [y/N] y
Deleted Volumes:
7812d609c2f2eccdf8ee2940c1780ecf4e3b0ea9447deab84037073b5e0c6a83
809b5ffbc4dac27d0ecb26e639acb3b12ced7a0a8f33489ad504e6603a6dd83d
blog_1_postgres_data
f7c5be6990c6b34f5e8443e1b1c7683f64e5ad1319beda61d27bb24ca03ee53c
fb6bed5dd41ef6a60f11bb26de5cf356c91c94e37b7334612f21e263dc94961b
d1882c8eafe88a738e23046ae9b109a8ee561de1fb3880a116d0f3b254c7034b
e887090deeb818a1728c2da519a84810ab6a9bfdd1d9a85cadd72882ecb7836c
ec00be94cccae8366b9e2dfa621984d048c86e37f4f4dfcd2a0e1d67e0163674
0caf0d3dd6a1a970523a96de822a28463b532d8d29f52a9118cca72e64f7f7f5
679b23cc64459cb49f872c1b7c5ec25685ba00fceb8422d4386fb4f238ae1602
8ea2f56df49ba43919338185f7ec631d3bbf27aa59d55f833da39e2e3aecbee2
a7aa142acec71f88d56ded866b22e0f1f11b51ae8634e4184174f84006e750d0
b7a01894ee9487de5eb6e71c83b83624906a9636c7049ce2ba6e255a8b8263fc
0e264b4024c75a758ba4d16f1039ccde7bf237e22c493ababaaf5d1b860df705
1cccea2ee721fe5c65812812694ff902a8f353d08cc3fb72b23306f3adad391f
61030e8a25717802318e9608b2a73fefb5a3828905e1068e51209ccaf332c806
ab2e1abec44cba3a313a37994e7ac97cba0fcf4b111438f57e308bfa481c30a0
aee8b9e7f3291f40e03295ad5588454b1624c1a556e7aa3eaf5efe22603b9e5e
f90423cd5e740af2fbdc4e466393f4235096c752f072d1f08388520af02612be
7d94a08c6d551ac1a251af99da5e19b596d6503012b5a4f46f7fcd85c53e6b06
811b678eafe0861e390f0ab0fdda28478583d2dfebd05281eb8eac82753b1335
bb1d86c363a407ffe20184ab4a3e039bd475d71977badbd556f7234665aca3b5
c386ba5218415695eba6bc726ad05ed2383e7d236f161cd057938ea8ecb88ed5
blog_postgres_data
e96a4470d7964c30720f6893f79c9b546613780d781dbb0027541ebd55bb4199
a3f6d2c8fad975aa480719623d0e4d541ba99f5e12362c9cd085c4b36a1a6b72
ba959df7199125ce2ba2f8093aab82245624258be661ea0ec4b1c5199595fba0
f3e8b7c28df24e7f4573a477c8ea79557638c5c6be67a73731a1083a298ef284
05ec27c77189526f2cc3906f45e025e6a7b345816fb319bfef0a5033e10294cf
2b83011785195240bc546ef25e7f264d872c00158b7a6ece6f5b595bc3013602
3547ccb6e2cbc18aac4a1b2fc8ab0869b0fec0c965fb322e1932d68984fe4dc8
579f9eaf9633a4701e93ce7516944d7d7586627d88efb21f4530cba1b2b33719
6f7f7f457608c51a78353afdc5dca647e70eef61899affb82843d7a7dcb801cc
4eb793c603a3150c612cb508d4be2016ec47666e06c818201bbcb3259b6924b8
5c648b8ccc88072ecb49c81028eecfdd0b1fb8151f1c43bee64e940431d36768
8a185034168b58c4a78a0c0dc2bc55abbd277cb0052cdf915681b321b4027bbb
92bd84a74a14d301154d7e090e5b8803e9b222c5853c91bc666381f1e658a308

Total reclaimed space: 2.428GB
Koitaro@MacBook-Pro-3 dockerfile-assignment-1 % docker system df
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              0                   0                   0B                  0B
Containers          0                   0                   0B                  0B
Local Volumes       0                   0                   0B                  0B
Build Cache         0                   0                   0B                  0B
```
