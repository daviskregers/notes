# Removing stopped continers

When there are a lot of stopped containers, basically all they do is taking up diskspace, there might be situations where we want to remove them not to leave them in a stopped state.

```
davis@davis-arch  ~  docker system prune
WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all dangling images
        - all dangling build cache
Are you sure you want to continue? [y/N] y
Deleted Containers:
0f4205a09dba73aa5604ef2cb06ab5a2dba054e42e44aa4d45d99b09e08da73d
aba242a52208c5b4a85239e697bba60db7d37faa0aae62d6975899cbb66a5eab
be33032ba83ec90e6606caa0aba75f7294ae63ea22f39cfbae54088b3f4749d8
28cade9f5e6b5ad8aba25b3686a97bc252fb0cf8442790846c7c9f75d474e4df
ceae74bbdb5a83e772edd3aaa9576a87d2aa8044aa579a263b3ced773ea5f97a
2b7ca645d6b876097a38d32e70c96f7b3227aefc64de72da2eea2b2dcacb359a
a90cda4fbf74c27bdca0dc679c9e9bf4c00fa4f4ab8fa38b4e39f57b6ac03ce4
49ca4be6a89a34ca9aa228ed3b2484fbbc95bc426dac8c2b626aa2b0270cf793
08a47054eeaada2fa5d347ac76a04b7268a6a9a96ba9a9624acc9c654d7a2f39
2395ab3de09720a306a0ac02a992457de6f95e8b7c25c890a7b27974babf089f
2fa3f86edaf83463f5abb7e00c04e920edddc5b84d237b3444d8c59a8297602e
f4dffbeae0e789aef9d22a48434c57a0489726a64add044a3e4b329273bb3c33
6a303e43cab76059acb99b9fa2f2348ed9474ca9620743aebc4e7ddacadde872
93ea0762aa3a6faedad37589c035a5cbb06b42e85cec5220780bb4388eacaeea
b793b6f258786e24e5807043993090bf448bd63efedde00536869fcf900784d8
f4942e7b3e0a79fceda64aaaae78579ff0daa97aaa99aaf9b636cca922a06daf
af4db85b936a228ea9a59ea7779d29db7e0acf980f29e34ea25a064aa53769cd
fcba457e7c30f058c55c6a0db609cc970a2fc06adcd60c386c85bcf3a89b6e87
54ceb98bd98c6dd2aa49c85edeed5efa756a9e255e9f7ace388babaafc0ecdf4
dc8c3b08ce482b646b5e52a85eb885a3ecf528b46277eaf5a4a4e0c0a988a62f
58caf8a72006c3fc3c50baf00dcc29abf5f94c4a48bafef43a37fa8b4784fc3e
f63a68bcbdf9aa0f3c4f448aa2fbb6ab8b0788b4aa22adc5b77c8a83943afe88
ed37a5766b29b724874a8baf7d9bc053aadcaa9a4f6ccf36e3d9d8a3afedc353
fa6303633ef4d4432a47ecc9a9897e37d6ebdcbb97528e2f8a0d8443b60c8d43
9c763dab4ecfb26ca4a89b568b96b25a7c2ff95fa0acfdca6c6a4fe26a8cb837
b0e8d00af5f6af235c3674a4ea844470bcf63a868866ca94ffc6d33e6a0ad9ca
d076a8584aa6d54fb2b3d5fbda9d6f7e7ba69ef3ba4a4803e88cddd2f820cfcf
005fd53362b244352ec7b37422b2f83ac40430d8da24355aee5726044f952efd
a4750034f8e0a300e4fcf57ec45ac5966d6e9f30ce08e070aebb723ffb85de20
6ee3bb3c083b000393c83ebf8c0e89c9fbcf5580cbea24b0dbc8c5ac5e26a2f5
ac004de38bca6bba52320b0da3044798ca56fbe4cd8a32c0a8d22558d9858e49
0ad58aa3538ba350badb6646eecc8805ee5b77697a4bc7a4c63b49228920bdea
95e6ba6726e3e0ca4a9a74a72b7290ad5ec66fcca92f2ad5d9f73252708f7689
70fbf74aa2ebc6eec68b9c20ec55ed0aa0978a4beea334f42aa2ad8ae5f5c578
f649899d4a7ccfe5a6ba25ab0ef78bc93ca0536473494f4a63edfca405076fbc

Deleted Networks:
x_default

Deleted Images:
deleted: sha256:0eba3eb9236934989d2d40d27c99e740c2dd062550fd0a6097de85b98addbdb0
deleted: sha256:ddef43bee7670933aa6ecbb6eed2934e8d03e2d37e80a27a5390ad8e85d8d4b4
deleted: sha256:47b6409dc054e7bcd64aa7c3ff76a6a99e52da24844d4d52ad3df68bd0a7697d
deleted: sha256:4c7fe7269ff7ed4aaee7fac95df7dff082c508aa4a5f059004fc879f29d67990
deleted: sha256:ba0874383a790785b5ddc483b76f5fda2f22cd40ca76652dffd8a564cfb4ad6e
deleted: sha256:3abefd83df96d69c80bf255027b508f3ad8d85bfddcc68f0c23cc6ddc890986e
deleted: sha256:53a06e8ce5b9d77f33d3567e76d33d2e40d3afb43ed2b7dd0430b383abbc7bed
deleted: sha256:04e56a5beebd4d773b2c569ed6782affb5d759fd9456745a665b722a6ec8efd5
deleted: sha256:e87b84d8efbcf9ba82aaafbdb5a9fc327a77d436060c0506ca5d567524df88ee
deleted: sha256:4f2d3c63d98e6debff3ee63a6dde748f46a2baec06d9d4577a4769562c944456
deleted: sha256:7fdb7fadf7dfe3d0dd96f26503bbbcc777dd7e635005d6220d4aacbfc5609d48
deleted: sha256:49be9bebfacf8bb3d5954047b7ed2aa62740cd3dcf3656efa93d5ecd02e757d6
deleted: sha256:03d664ff35057d7b90c7066038a3ea699c7b6728a5adad4525c5dc9cdc27ecbf
deleted: sha256:67b6f694854fd5bee83b6b2bd9df40d944b6a993fe053694294ca3a8c66f4307
deleted: sha256:7f43dc6ddd6568fca99563d2765d8fbd6cdb56a83e76ade00d0df6a6a2ee6b39
deleted: sha256:f3f9fd32c6807b2d04d6eb03a8c6e6025d73370d02d5be3d4fd7b859d2ebd0eb
deleted: sha256:398abaddcb52f3c357d055cadbddd3d5bf3e97a4d08b0dea53d66bd962d2892c
deleted: sha256:a7d09aafd8df8247debdd504ef2ee3042a3df0667fec7f295b9edf8c8aa98622
deleted: sha256:b740744a6532d09d2d82dc2e644ec28ec79a5d9c453dff9d72bbda57f0f4d7da
deleted: sha256:5b3cde7b97370d65f782e2486e4bebd4b048dda5cb05d023520f82863520ed0a
deleted: sha256:deacb673d4df65a2ddd8de757b333d37e059dd0c8b72676e5dc8867e0faaac45
deleted: sha256:3aa07addf85d8b63dee7d96332f9ecd323ed0addc4bd5edaa0accedabcd3ecf2
deleted: sha256:e2c77269e6d8393089fd2acdd8c2d5febe8a20ddfdbb35f9f9dd2ca7d2d247d5
deleted: sha256:b6eab3fe6e00e433ceafffcdcede968a33b5dcab26dadbb9c4ea72992d752fc8
deleted: sha256:5a99723f049d9d262d7209983cd6e0f2d35a9ebdeffae6d8d3098e8a2dbde049
deleted: sha256:860c8bb03e7dd50d2babd09abbd6fdd3dbee8f93d64b3c7ed7e29a2be8eef7bb
deleted: sha256:98f80059f92d58aa9ca756fad949df33df35036afd682eee230b68682f2eb5b8
deleted: sha256:cb285b4defdc2de649490a6d3dfd67f6fcad8f2da3df22725d44dec9e35bf066
deleted: sha256:04ddb2eb40ddd5700ddc7dfdf9c4847d65cdf959c0592c4acbd9726e9e659e92
deleted: sha256:bf9bb0cbc545e8b368f76dcec843ad0dfc590ddd0c8657b82becfafddae24452
deleted: sha256:cd8947d6cdb0f5b28bdf747df9896947098bd00834944c5db4982de8d39d6ffd
deleted: sha256:5dc75c08b4db43de7b8399def9063af0fb4fff9548cbf0cdaeeb8a427bce439c
deleted: sha256:99fc56305ff7b00293dcd3bb324679edab7e39dd077b90949ac7d5ca9da7b934
deleted: sha256:03daf335d82be22d7f304cafb887dd9acadd244beedd0434f6b46226579b7d39
deleted: sha256:fc83657660cb03af32bcb8b626ca0f44735be3cb6e7e7e8a3ddb6b9edd0389d8
deleted: sha256:2525deddd2ddc87402459ac4ba2376c88e52dfc9de0ee3bebbe9287d675b0066
deleted: sha256:d0c0a6f50d5dbded67576d45f4d79d0237d067895d9e27a0287e7f4bda9d49eb
deleted: sha256:0d956dbb67dc9ac967bb835088865af28cd5a4b363305ec4f8d5d3f204cf70bc
deleted: sha256:bb075d2fc3a6ad24529cb6dfcc67ec6583a995f7d97ac8c7efb9dd473d384b2f
deleted: sha256:d9a9edeb3032be72eaddd0e64e7b954b4dfb4d6dd9aa206d2402a92490beb903
deleted: sha256:0dd7da6372208cb4b370fc530c75d7d22dd53393db83eedd48502db4de9f6476
deleted: sha256:2695fd6226646e85d3343594c64aab8aa7094d6a7cbdedf8b622b474ba20d8f4
deleted: sha256:62cc327d4d08e46490ddd6032b59ce605429d2d79c750bc0db4fdfdfb8c6dcd5
deleted: sha256:6d3d54075adcd65ad6980df23f55f35bcf0ed32958235ce404b2d477e92ad0bd
deleted: sha256:9af70efd0c0eed8aa7854de0c6822cfd82ea7b830020d4948bc789d299428063
deleted: sha256:ed6dc2539323358cc3b8cc504d2c4523fba07dcdd255d4dc7deb32202bd686ac
deleted: sha256:abd66bc79558e9638cc7d8a7824fd2823d3b423c6c2f9b2f7d22fdd0d46c4aef
deleted: sha256:b90343064f3bcbb2e9c544539e2dbcbf9fdc954f8767a955cc46c08c75aab9dd
deleted: sha256:e24ef2dce7ae9eaf0392baa06575685656cd5f833a5ccab060f64d493da2e034
deleted: sha256:8d8b729a262f048a75fc49b282892faada09c85d94a3da86d7a66724989a2c8a
deleted: sha256:a6f7fa296775e0a9e7773f7d7a4b9a566b689227dfa27a4aff3638acd446e235
deleted: sha256:0dbbd9405f6ba039bac0964ad678609c98eb5f35a2ee73c5a5fcdffaab7889a8

Total reclaimed space: 568.2MB
 davis@davis-arch  ~  
```

Now we can check the `docker ps --all` and we'll see only our running containers:

```
davis@davis-arch  ~  docker ps --all
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
3d2bac4adcd0        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-frontend_run_71ec1574b4b9
7ef2e25bde57        x-api        "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-api_run_706c3e49d578
a39d737fc13f        x-frontend   "sh -c /var/www/dock…"   7 days ago          Up Less than a second           80/tcp                    x-frontend_run_6e04a848228d
60fd1cceaf76        redis:alpine                   "docker-entrypoint.s…"   7 days ago          Up Less than a second           0.0.0.0:6379->6379/tcp    redis
d1aafec6bbdb        jwilder/nginx-proxy            "/app/docker-entrypo…"   7 days ago          Up Less than a second           0.0.0.0:80->80/tcp        nginx-proxy
dc9f43f8754f        redis                          "docker-entrypoint.s…"   2 weeks ago         Up Less than a second           0.0.0.0:63791->6379/tcp   x_redis_1
e6615103591f        mariadb:latest                 "docker-entrypoint.s…"   3 weeks ago         Restarting (1) 21 seconds ago                             mysql
```