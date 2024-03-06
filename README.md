![SEAMAPD21 Project Image](https://github.com/SEFSC/SEAMAPD21/blob/main/resource/seamapd21_bg_1091_326.png?raw=true)
Here we present the first large-scale, fine-grained reef fish dataset from the Gulf of Mexico - the Southeast Area Monitoring and Assessment Program Dataset 2021 (SEAMAPD21).

Automated image analysis of reef fish species in challenging environments, such as coastal Gulf of Mexico, are crucial for accurate fishery monitoring and stock assessments. As advanced computer vision techniques evolve in precision and capacity, previously difficult tasks such as fish species identification and count due to strong intra-species similarities and inter-species variations, have become feasible.

SEAMAPD21 was created to enable fishery scientists and researchers to process raw image-based data at high volumes at a much quicker rate than current manual methods. This open-source dataset contains 90,000 annotations for 130 species of fish from two annual surveys done in 2018 and 2019 in strategic areas of the Gulf of Mexico using baited remote underwater video systems to assess reef fish populations. We perform baseline experiments and document predictive classification results.

### File Notes
26GB of data split into 263 tar.gz files. Direct links to download the files are below. It's likely easier to run the wget script (in the repo) to download these files. <b>NOTE:</b> Once downloaded they must be merged and un-tar'd using a command like:
```
cat SEAMAPD21.tar.gz* | tar xzvf -
```

#### CSV Files

The CSV files are **[VIAME](https://www.viametoolkit.org/) CSV** files: system default comma separated value [detection file format](https://viame.readthedocs.io/en/latest/section_links/detection_file_conversions.html). Summarizing the [docs](https://viame.readthedocs.io/en/latest/section_links/detection_file_conversions.html#integrated-detection-formats):

There are three parts to a VIAME csv. First, nine required fields, comma seperated, with a single line for either each detection, or each detection state, in a track:

| Column | Contents | Description |
|:------:|----------|-------------|
| 1 | Detection or Track Unique ID | Can be used to link detections from multiple frames onto tracks |
| 2 | Video or Image String Identifier | Video timestamp or an image filename |
| 3 | Unique Frame Integer Identifier | Unique 0-based frame identifier for the frame in the given video or loaded sequence |
| 4 | TL-x | Top left *x* coordinate of the target bounding box in the imagery (top left of the image is the origin: 0,0) |
| 5 | TL-y | Top left *y* coordinate of the target bounding box in the imagery |
| 6 | BR-x | Bottom right *x* coordinate of the target bounding box in the imagery |
| 7 | BR-y | Bottom right *y* coordinate of the target bounding box in the imagery |
| 8 | Auxiliary Confidence  | Context-dependent (image or video): How likely this detection is an object, or the confidence in the length measurement, if present |
| 9 | Target Length | If not present, specified with a value less than 0, most commonly “-1”|

Detections can be linked onto tracks on multiple frames via sharing the same track ID field. Next, a sequence of optional species <=> score pairs, also comma seperated:

| Column | Contents | Description |
|:------:|----------|-------------|
| 10 |  Class-name, object 1 |  Optional species ID |
| 11 |  Score, object 1 |  Optional species score |

There can be as many class, score pairs as necessary (*e.g.*, fields 12 and 13, 14 and 15, *etc.*). In the case of tracks, which may span multiple lines and thus have multiple probabilities per line, the probabilities from the last state in the track should be treated as the aggregate probability for the track and it’s okay for prior states to have no probability to prevent respecifying it. In the
class and score list, the highest scoring entries should typically be listed first.

Lastly, optional categorical values associated with each detection in the file
after species/class pairs. Attributes are given via a keyword followed by any
space seperate values the attribute may have. Possible attributes are:

| Attribute | Possible Values | Description |
|:---------:|-----------------|---|
| (kp) | head 120 320 | Optional head, tail, or arbitrary keypoints |
| (atr) | is_diseased true | Attribute keyword then boolean or numeric value |
| (note) | this is a note | Notes take no form just can’t have commas |
| (poly) | 12 455 40 515 25 480 | A polygon for the detection |
| (hole) | 38 485 39 490 37 470 | A hole in a polygon for a detection |
| (mask) | ./masks/mask02393.png | A reference to an external pixel mask image |

Throwing together all of these components, an example line might look like:

    1,image.png,0,104,265,189,390,0.32,1.5,flounder,0.32,(kp) head 120 320

This file format is supported by most GUIs and detector training tools. It can be used via specifying the `viame_csv` keyword in any readers or writers.

### Data Downloads
|  Download           | Size       | MD5                              |
|---------------------|------------|----------------------------------|
| [SEAMAPD21.tar.gz.aa](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.aa) | 104857600 | d5bbb90b1c150e732a6ad4ef049c1836 |
| [SEAMAPD21.tar.gz.ab](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ab) | 104857600 | b70b1fb003a8c95fb002330fb274b407 |
| [SEAMAPD21.tar.gz.ac](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ac) | 104857600 | 26c720f55f85c08a3446d241d03c9870 |
| [SEAMAPD21.tar.gz.ad](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ad) | 104857600 | dc99d4fa4fa33392d35981b322fbfb71 |
| [SEAMAPD21.tar.gz.ae](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ae) | 104857600 | 7cf33fd8cf8059263e29fb57896d13d5 |
| [SEAMAPD21.tar.gz.af](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.af) | 104857600 | fb7107599f0e98510ae16be1a5f25816 |
| [SEAMAPD21.tar.gz.ag](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ag) | 104857600 | 4fa418d21a4c20b0fd105245f5b9e05e |
| [SEAMAPD21.tar.gz.ah](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ah) | 104857600 | 580911cbca3697d93fd37dfc7c99fda8 |
| [SEAMAPD21.tar.gz.ai](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ai) | 104857600 | d072879b6f26e567ce917bb767645834 |
| [SEAMAPD21.tar.gz.aj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.aj) | 104857600 | dc52403ddbf18f3e1c22edeff8e01d47 |
| [SEAMAPD21.tar.gz.ak](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ak) | 104857600 | 45ad1c11f1a2d2f8062640928fe25bc2 |
| [SEAMAPD21.tar.gz.al](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.al) | 104857600 | 970f87ace2956dfdd5279ca14e3a88ac |
| [SEAMAPD21.tar.gz.am](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.am) | 104857600 | 98d46017ae74eb6efdba2a053d3c244e |
| [SEAMAPD21.tar.gz.an](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.an) | 104857600 | 09a50a417b9e5308a4f59c2d079a5d21 |
| [SEAMAPD21.tar.gz.ao](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ao) | 104857600 | e93027db52d1bf5e68d30482ecd4b06a |
| [SEAMAPD21.tar.gz.ap](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ap) | 104857600 | f3825186026dfce6c2444eea038bbf4f |
| [SEAMAPD21.tar.gz.aq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.aq) | 104857600 | 7657855a121e75cea08840503cc44794 |
| [SEAMAPD21.tar.gz.ar](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ar) | 104857600 | 8239f2e407a8d2591c7b6f03720ffafa |
| [SEAMAPD21.tar.gz.as](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.as) | 104857600 | 487b09a1f678cbfe6a1848d6fa36d023 |
| [SEAMAPD21.tar.gz.at](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.at) | 104857600 | a6d390924988b0ed7f9dfc3113b1b464 |
| [SEAMAPD21.tar.gz.au](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.au) | 104857600 | 4b518b6e8b8f029934528241ef4acf88 |
| [SEAMAPD21.tar.gz.av](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.av) | 104857600 | 7bf798c9e3faba3ab6ffc6b2464a3332 |
| [SEAMAPD21.tar.gz.aw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.aw) | 104857600 | 6b585da2f391a47b93599f197bb6d806 |
| [SEAMAPD21.tar.gz.ax](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ax) | 104857600 | ce76a86c4f94de2224b80b087f14687e |
| [SEAMAPD21.tar.gz.ay](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ay) | 104857600 | 52a5b3afeb2a1122904933ace70b32be |
| [SEAMAPD21.tar.gz.az](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.az) | 104857600 | b1e96e4490306d955d33c58c1ada18c7 |
| [SEAMAPD21.tar.gz.ba](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ba) | 104857600 | e9f2cbd26d972e62b0b67dc70e74e7a4 |
| [SEAMAPD21.tar.gz.bb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bb) | 104857600 | b5060acd7dabb22ef4262032ffa2807e |
| [SEAMAPD21.tar.gz.bc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bc) | 104857600 | 3bc38b036aa716c9749bbf668440f094 |
| [SEAMAPD21.tar.gz.bd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bd) | 104857600 | 5df9dd150ab1892e10267c87409d8ffd |
| [SEAMAPD21.tar.gz.be](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.be) | 104857600 | e94a98c6dd8ed64b1a91463dfcc93e4c |
| [SEAMAPD21.tar.gz.bf](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bf) | 104857600 | 27d9180d63149d3dd60f95a502e49782 |
| [SEAMAPD21.tar.gz.bg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bg) | 104857600 | 26e498e15fe3ac3c18eaf482eb803be6 |
| [SEAMAPD21.tar.gz.bh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bh) | 104857600 | e94c0428d3e0edb3972ead547e3a8f54 |
| [SEAMAPD21.tar.gz.bi](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bi) | 104857600 | 0fed70ab9f517617dfa7168c947e25d7 |
| [SEAMAPD21.tar.gz.bj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bj) | 104857600 | 8cd52e1f1633e55c84ea9a7d8101eece |
| [SEAMAPD21.tar.gz.bk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bk) | 104857600 | 445d6c9debd2671c40b2e685b8f0e82c |
| [SEAMAPD21.tar.gz.bl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bl) | 104857600 | a53b27aa13210c02e3f618d6a29557e5 |
| [SEAMAPD21.tar.gz.bm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bm) | 104857600 | 3254ce90ebfd1c552f785a10c419535c |
| [SEAMAPD21.tar.gz.bn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bn) | 104857600 | 7429b2bc9683fee46bdaca55592a791c |
| [SEAMAPD21.tar.gz.bo](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bo) | 104857600 | 889bdbfb5ee15b500d1da7f39134c03e |
| [SEAMAPD21.tar.gz.bp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bp) | 104857600 | 20f0e6622f55bda8ea18b7fb1c24953d |
| [SEAMAPD21.tar.gz.bq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bq) | 104857600 | 14a1b3c656949e76228f33bf386706e1 |
| [SEAMAPD21.tar.gz.br](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.br) | 104857600 | b59427eba17e6a816895cf0de24d0a32 |
| [SEAMAPD21.tar.gz.bs](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bs) | 104857600 | 2fbe943eb401f511388f8f90ce46ea8f |
| [SEAMAPD21.tar.gz.bt](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bt) | 104857600 | e9216b5614e4f3d8d061b6e0bf7349de |
| [SEAMAPD21.tar.gz.bu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bu) | 104857600 | 57d4cc2951924a1b6604bfb70a334483 |
| [SEAMAPD21.tar.gz.bv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bv) | 104857600 | 7ec22135e8fc3565fa5c1ab5b4367c7b |
| [SEAMAPD21.tar.gz.bw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bw) | 104857600 | 5f5a53172fd1565971a84e871baeb014 |
| [SEAMAPD21.tar.gz.bx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bx) | 104857600 | 9324e830ac8e8596624e64cf5557fa48 |
| [SEAMAPD21.tar.gz.by](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.by) | 104857600 | 16903e58ffb0315252a649c10d10634e |
| [SEAMAPD21.tar.gz.bz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.bz) | 104857600 | c010776fc558e04de9cad2a543a1ae45 |
| [SEAMAPD21.tar.gz.ca](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ca) | 104857600 | acf3cc66ca7819d5a37594757f90abbe |
| [SEAMAPD21.tar.gz.cb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cb) | 104857600 | 7afee2ef1f6a0c078a77eb5eb3da5e0b |
| [SEAMAPD21.tar.gz.cc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cc) | 104857600 | 88017e5a38ee558c728fee7c39686023 |
| [SEAMAPD21.tar.gz.cd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cd) | 104857600 | 51e0b150ced338ed4c509fd7334eded2 |
| [SEAMAPD21.tar.gz.ce](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ce) | 104857600 | c02c3743a6aa4fda1d773efb8843d03e |
| [SEAMAPD21.tar.gz.cf](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cf) | 104857600 | 93b0d642c9adacbf6fdd520dc3c6ae3b |
| [SEAMAPD21.tar.gz.cg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cg) | 104857600 | 5fa7251220abdcf0739723fae13e3baf |
| [SEAMAPD21.tar.gz.ch](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ch) | 104857600 | 2b06eaae3da4db8dc6606a0eae3aa030 |
| [SEAMAPD21.tar.gz.ci](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ci) | 104857600 | 2861475d61c0a216cf033f419ec59dcf |
| [SEAMAPD21.tar.gz.cj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cj) | 104857600 | 7e58ff53566d47db2549b9a58209672c |
| [SEAMAPD21.tar.gz.ck](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ck) | 104857600 | 03ef29f7a33063feed94d0d1ce782c0d |
| [SEAMAPD21.tar.gz.cl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cl) | 104857600 | c151cefdf4ae1022ef3208c28f8f7d8b |
| [SEAMAPD21.tar.gz.cm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cm) | 104857600 | 53e1018ef59d3543fc1209482e712ba3 |
| [SEAMAPD21.tar.gz.cn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cn) | 104857600 | 7799992667687f5a74edf91bc6555bb0 |
| [SEAMAPD21.tar.gz.co](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.co) | 104857600 | 11864a3e47e18ee65d6996f1431c294c |
| [SEAMAPD21.tar.gz.cp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cp) | 104857600 | 6c060f1f323fcfa87ad9d193d39ba590 |
| [SEAMAPD21.tar.gz.cq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cq) | 104857600 | bf390a41d2a11ad7b69c5af915822044 |
| [SEAMAPD21.tar.gz.cr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cr) | 104857600 | 34a88d60f89e1f9b1b020be9b6a4457f |
| [SEAMAPD21.tar.gz.cs](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cs) | 104857600 | 4b9874ccb4f1ea4a314f79981c9a0daa |
| [SEAMAPD21.tar.gz.ct](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ct) | 104857600 | f8114f85754d26344d32d2cd9539d696 |
| [SEAMAPD21.tar.gz.cu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cu) | 104857600 | fc378e6e799e69ef19a17a4e1ae9cf36 |
| [SEAMAPD21.tar.gz.cv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cv) | 104857600 | 4738ff770c51f28edef9a2027160ec80 |
| [SEAMAPD21.tar.gz.cw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cw) | 104857600 | 58ae178aff9319a414d5c7ffe9821457 |
| [SEAMAPD21.tar.gz.cx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cx) | 104857600 | 9d6318d3b8da2025fbf91d0fd52b6ef4 |
| [SEAMAPD21.tar.gz.cy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cy) | 104857600 | b41f361bdb12b5d2b474c3dae489d98c |
| [SEAMAPD21.tar.gz.cz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.cz) | 104857600 | 70ea1b64d3991edb19a6ef564d25d8b7 |
| [SEAMAPD21.tar.gz.da](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.da) | 104857600 | 4e975cd58f04b158a7f50fec63a962c6 |
| [SEAMAPD21.tar.gz.db](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.db) | 104857600 | 50152390dd96f246cb29a60c53c1603a |
| [SEAMAPD21.tar.gz.dc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dc) | 104857600 | e06bcd1b5413ffc597aa4beb5599123b |
| [SEAMAPD21.tar.gz.dd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dd) | 104857600 | 4d0ec846a8fd2bc07a04dc9dc4d55b8c |
| [SEAMAPD21.tar.gz.de](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.de) | 104857600 | db5e27261185c52a06042d0eadf8fe91 |
| [SEAMAPD21.tar.gz.df](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.df) | 104857600 | d3587aadb7728d7223118bf1f2121d2a |
| [SEAMAPD21.tar.gz.dg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dg) | 104857600 | 735d8aa1a6e078445ba8dafe93ba07be |
| [SEAMAPD21.tar.gz.dh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dh) | 104857600 | a361abab2e9c3f35b95192db4ac5cfa1 |
| [SEAMAPD21.tar.gz.di](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.di) | 104857600 | 20364d601978b38435e0d15b8f92da8b |
| [SEAMAPD21.tar.gz.dj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dj) | 104857600 | 4d0f2e2ede7b4fddf2c099ad64acaaa7 |
| [SEAMAPD21.tar.gz.dk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dk) | 104857600 | cb20d64807caae8f71fb115867a61683 |
| [SEAMAPD21.tar.gz.dl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dl) | 104857600 | 70a540d8673216f7b3e33f9866b89106 |
| [SEAMAPD21.tar.gz.dm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dm) | 104857600 | 264aff322f38f78175a4f88dd31b4b48 |
| [SEAMAPD21.tar.gz.dn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dn) | 104857600 | 1c5ece6bbbf14ea6e5754e81e00e4d25 |
| [SEAMAPD21.tar.gz.do](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.do) | 104857600 | 4267d78dfcad3600343fef559fecd0d6 |
| [SEAMAPD21.tar.gz.dp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dp) | 104857600 | cee0682f14d76253610f2f36a24b541c |
| [SEAMAPD21.tar.gz.dq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dq) | 104857600 | 8270413fef47f83ee1fa1d722e3a246e |
| [SEAMAPD21.tar.gz.dr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dr) | 104857600 | 6ff59e7f5a4332027666f9180a300934 |
| [SEAMAPD21.tar.gz.ds](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ds) | 104857600 | 9463796e0ff3a013fb3cc5686a120c4d |
| [SEAMAPD21.tar.gz.dt](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dt) | 104857600 | 38cb25c37030d29fa9e754921d443e96 |
| [SEAMAPD21.tar.gz.du](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.du) | 104857600 | f47ac5b8e0987591e11763c653900aaa |
| [SEAMAPD21.tar.gz.dv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dv) | 104857600 | 958b61c6c0cb07b1cf502c75515c38a9 |
| [SEAMAPD21.tar.gz.dw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dw) | 104857600 | 3a706dd9fdf644e92719dae569295242 |
| [SEAMAPD21.tar.gz.dx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dx) | 104857600 | 43186db66650bfb27cae625f3e744700 |
| [SEAMAPD21.tar.gz.dy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dy) | 104857600 | b2572861c5987a328c9205d8385e02ae |
| [SEAMAPD21.tar.gz.dz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.dz) | 104857600 | 42641051ee3f51d452a1930ff8dc0e73 |
| [SEAMAPD21.tar.gz.ea](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ea) | 104857600 | cd55ef9d45b1d1bb31606c611e26ee07 |
| [SEAMAPD21.tar.gz.eb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eb) | 104857600 | 10d51fadc2055f56d586c00d56732378 |
| [SEAMAPD21.tar.gz.ec](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ec) | 104857600 | 55fc9d1465ac866696cdef7cc4986e38 |
| [SEAMAPD21.tar.gz.ed](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ed) | 104857600 | edaac35679fbebaee319151340149271 |
| [SEAMAPD21.tar.gz.ee](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ee) | 104857600 | f71c71f4421e8ea21f425fd5745e7345 |
| [SEAMAPD21.tar.gz.ef](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ef) | 104857600 | 2e986c62ae3114e443311fff01c28cf5 |
| [SEAMAPD21.tar.gz.eg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eg) | 104857600 | c2b8bf12ab346f76fce60c7e8075b03a |
| [SEAMAPD21.tar.gz.eh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eh) | 104857600 | bc559045fa504c1998a7f51e969ae958 |
| [SEAMAPD21.tar.gz.ei](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ei) | 104857600 | 637ac389ee35d9e2db7680393a87f8c6 |
| [SEAMAPD21.tar.gz.ej](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ej) | 104857600 | 32800419b1d514d2bdc38c047f4ab734 |
| [SEAMAPD21.tar.gz.ek](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ek) | 104857600 | 1f4b832339dc05b74cc53e1aefa1c731 |
| [SEAMAPD21.tar.gz.el](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.el) | 104857600 | 963bd0ffb4ea17cecc2825224a33e019 |
| [SEAMAPD21.tar.gz.em](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.em) | 104857600 | 24fdd4c86d44841c0be5b7a865981f3f |
| [SEAMAPD21.tar.gz.en](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.en) | 104857600 | c26f3ae903a1d0278e3c437446d11ccb |
| [SEAMAPD21.tar.gz.eo](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eo) | 104857600 | 65bfce907a89f286bdbb16924dbaeef9 |
| [SEAMAPD21.tar.gz.ep](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ep) | 104857600 | c5e2fd87ee2789c150667795614c3614 |
| [SEAMAPD21.tar.gz.eq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eq) | 104857600 | 9d8fe222d86c1f2419da3b2664e57378 |
| [SEAMAPD21.tar.gz.er](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.er) | 104857600 | 1e0925d4a1c554e4cbfe218e511ccc1f |
| [SEAMAPD21.tar.gz.es](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.es) | 104857600 | a773bf44b6ac0065b62872fb7f3f5b1d |
| [SEAMAPD21.tar.gz.et](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.et) | 104857600 | e09fd4295c09054427c5a16bd259b6e7 |
| [SEAMAPD21.tar.gz.eu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.eu) | 104857600 | 85e089880f677b14ce3ee4bc78c63394 |
| [SEAMAPD21.tar.gz.ev](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ev) | 104857600 | 71d1d865d97be3d536b3c370a4e0db42 |
| [SEAMAPD21.tar.gz.ew](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ew) | 104857600 | 59bf04aaef04534d167c094e38f12807 |
| [SEAMAPD21.tar.gz.ex](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ex) | 104857600 | 8b15a50891ecbae3bc8fc498430d9cb8 |
| [SEAMAPD21.tar.gz.ey](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ey) | 104857600 | dc46a78e14cec95201c99a8a7270ab2f |
| [SEAMAPD21.tar.gz.ez](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ez) | 104857600 | 8ee2a9cd11e0c435090cdaa0561afceb |
| [SEAMAPD21.tar.gz.fa](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fa) | 104857600 | 46046ed9faa82c1120ea1cbeef68bb0b |
| [SEAMAPD21.tar.gz.fb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fb) | 104857600 | 0346f2dc3dca00ef0d8e52f148851bd1 |
| [SEAMAPD21.tar.gz.fc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fc) | 104857600 | 1dbb18e9d11909d445f1d3900e488f55 |
| [SEAMAPD21.tar.gz.fd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fd) | 104857600 | 528e91a36501b7bf587f7c2a34a92b76 |
| [SEAMAPD21.tar.gz.fe](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fe) | 104857600 | 4db95552a1f9f00118a57e20e64b4159 |
| [SEAMAPD21.tar.gz.ff](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ff) | 104857600 | 0558747226918057715b25ee3742e270 |
| [SEAMAPD21.tar.gz.fg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fg) | 104857600 | 98ee1370997202f145064ea6698cb7d5 |
| [SEAMAPD21.tar.gz.fh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fh) | 104857600 | 5c5adb932fb5f4307d33d1a346147a5e |
| [SEAMAPD21.tar.gz.fi](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fi) | 104857600 | 420efcb47f5793898d075146ee19b2c2 |
| [SEAMAPD21.tar.gz.fj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fj) | 104857600 | ad9cc8e60997642d82acb936c50342aa |
| [SEAMAPD21.tar.gz.fk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fk) | 104857600 | b62367f74d614ba6858e4f09732f2749 |
| [SEAMAPD21.tar.gz.fl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fl) | 104857600 | e505ab869e8870aa53e7da9c38f51f72 |
| [SEAMAPD21.tar.gz.fm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fm) | 104857600 | c5fb9178d64343030a99ce2574bd04dd |
| [SEAMAPD21.tar.gz.fn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fn) | 104857600 | 8ca7720d8701b72cb2fb6d53acf6bc49 |
| [SEAMAPD21.tar.gz.fo](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fo) | 104857600 | acbaeb3005b8f466f3df95524399b0d4 |
| [SEAMAPD21.tar.gz.fp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fp) | 104857600 | 7fcfdc1e562032463c1fec66b39742aa |
| [SEAMAPD21.tar.gz.fq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fq) | 104857600 | 57264417c4caae9c73dfcf28d7010c12 |
| [SEAMAPD21.tar.gz.fr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fr) | 104857600 | 44ae13cd9da95fdd3ca7f618ef92ce2d |
| [SEAMAPD21.tar.gz.fs](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fs) | 104857600 | cfb26463824c49f50ec235e4abbf8107 |
| [SEAMAPD21.tar.gz.ft](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ft) | 104857600 | a735b1d97d6e58d936799c6474c20954 |
| [SEAMAPD21.tar.gz.fu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fu) | 104857600 | 8a7888f0a00c60d8b17bc9d4e558fa68 |
| [SEAMAPD21.tar.gz.fv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fv) | 104857600 | 25968d027a3bb166817682179b3f2bfa |
| [SEAMAPD21.tar.gz.fw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fw) | 104857600 | 8b0ef4564790c409d218309a83019236 |
| [SEAMAPD21.tar.gz.fx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fx) | 104857600 | 827677f9853908940a364f10bbedf2be |
| [SEAMAPD21.tar.gz.fy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fy) | 104857600 | 7efa41a73e42c7e86c93ad36a235fec5 |
| [SEAMAPD21.tar.gz.fz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.fz) | 104857600 | 00a35cbc662ed439987b742ab6bcc9bb |
| [SEAMAPD21.tar.gz.ga](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ga) | 104857600 | 266988a7589ef103714ab5e9b1420a02 |
| [SEAMAPD21.tar.gz.gb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gb) | 104857600 | 50c3a30565aa1acce0c4c88c734ecc26 |
| [SEAMAPD21.tar.gz.gc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gc) | 104857600 | 5f1baac4a21b9b744b4ea3afda799a6f |
| [SEAMAPD21.tar.gz.gd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gd) | 104857600 | 3a400423452af4032eae10f453ad4542 |
| [SEAMAPD21.tar.gz.ge](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ge) | 104857600 | 0a16715c56298669c2a0aa81b9145e91 |
| [SEAMAPD21.tar.gz.gf](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gf) | 104857600 | 223d3ecd564e85c4ad90d9159cf831fa |
| [SEAMAPD21.tar.gz.gg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gg) | 104857600 | 33dd1a4d38f3113049b51ddd3d3d6b9e |
| [SEAMAPD21.tar.gz.gh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gh) | 104857600 | d4e01630ccc6ffc7a4182a524ba598f0 |
| [SEAMAPD21.tar.gz.gi](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gi) | 104857600 | 08f385a6c77a353e6aae059fde7e1017 |
| [SEAMAPD21.tar.gz.gj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gj) | 104857600 | 2bdfabf4d6bf72c1cb2e47ecab57f0c1 |
| [SEAMAPD21.tar.gz.gk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gk) | 104857600 | 3447b94f049ac4088833ad1201bc0aea |
| [SEAMAPD21.tar.gz.gl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gl) | 104857600 | a5a494888061043f181134579f7e1fa5 |
| [SEAMAPD21.tar.gz.gm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gm) | 104857600 | 3f2987fdd3962e51287d8030c11b40bc |
| [SEAMAPD21.tar.gz.gn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gn) | 104857600 | 14ad62f022caae04b4e177b843021a1c |
| [SEAMAPD21.tar.gz.go](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.go) | 104857600 | 74c23226e2eaf4c37023e82a186a2a94 |
| [SEAMAPD21.tar.gz.gp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gp) | 104857600 | be46091da57c7dd874aa165ae1102899 |
| [SEAMAPD21.tar.gz.gq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gq) | 104857600 | 8f686afab25076eea3b38341b0bf596b |
| [SEAMAPD21.tar.gz.gr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gr) | 104857600 | 323341ea7ef22da3b9d94e962fa04940 |
| [SEAMAPD21.tar.gz.gs](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gs) | 104857600 | d5ea1b8f1b1ae053366761538f0fed49 |
| [SEAMAPD21.tar.gz.gt](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gt) | 104857600 | 8b668f2eb60f9ee1a0644f1c5d3b5c2b |
| [SEAMAPD21.tar.gz.gu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gu) | 104857600 | ae1eaa5d35e85578e3d2e4acbb7926a1 |
| [SEAMAPD21.tar.gz.gv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gv) | 104857600 | 801dd70302628d35dbddd5b222ef9df5 |
| [SEAMAPD21.tar.gz.gw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gw) | 104857600 | 08fe3b7843d26a5f04595e8f192c8b81 |
| [SEAMAPD21.tar.gz.gx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gx) | 104857600 | 779db87f9ca9f038905e20bbc85dbb73 |
| [SEAMAPD21.tar.gz.gy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gy) | 104857600 | 532a2f94dcca164ff4176799683a8422 |
| [SEAMAPD21.tar.gz.gz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.gz) | 104857600 | 512c1c33dea2ddf6dba681932a1bf863 |
| [SEAMAPD21.tar.gz.ha](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ha) | 104857600 | ac38a2077aa233835d74a5d66f99c9a0 |
| [SEAMAPD21.tar.gz.hb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hb) | 104857600 | 0033e4dc6339cf1be7c650e62bbb21f3 |
| [SEAMAPD21.tar.gz.hc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hc) | 104857600 | 6a44f3222b92570159981990856f586b |
| [SEAMAPD21.tar.gz.hd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hd) | 104857600 | af11c2aa821c35b5905c597449f5c924 |
| [SEAMAPD21.tar.gz.he](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.he) | 104857600 | 97077522b70dcda6643031b70e2d45e3 |
| [SEAMAPD21.tar.gz.hf](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hf) | 104857600 | c19ebae3ac2f7fc8602db2e9f4fa6c2f |
| [SEAMAPD21.tar.gz.hg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hg) | 104857600 | edd4a730296f3032eaf79b0e103bf2db |
| [SEAMAPD21.tar.gz.hh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hh) | 104857600 | 63c4de4d92f13f00d29e8f7a372acc71 |
| [SEAMAPD21.tar.gz.hi](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hi) | 104857600 | 04853fd90f936c2936153b70a4669bac |
| [SEAMAPD21.tar.gz.hj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hj) | 104857600 | 2703707f15a97c77603deb5de2ddbb8a |
| [SEAMAPD21.tar.gz.hk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hk) | 104857600 | 4758eba70fabb34eb4c8c85766b1f36a |
| [SEAMAPD21.tar.gz.hl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hl) | 104857600 | a62b335936402f3dda6d6aa759a409a5 |
| [SEAMAPD21.tar.gz.hm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hm) | 104857600 | dcf0615fe77798904c6781078b5b5ec5 |
| [SEAMAPD21.tar.gz.hn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hn) | 104857600 | 2cfda66c906ef22f4a619285583d1d22 |
| [SEAMAPD21.tar.gz.ho](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ho) | 104857600 | cd7e7f6fc010052450b32d2d5f58c9ad |
| [SEAMAPD21.tar.gz.hp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hp) | 104857600 | c38ea01216215eaa4d5486549c499e1a |
| [SEAMAPD21.tar.gz.hq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hq) | 104857600 | 723d751fc7d286d9afc206de895846df |
| [SEAMAPD21.tar.gz.hr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hr) | 104857600 | 5087af6707efa2f3bc6d7b9f8c81b703 |
| [SEAMAPD21.tar.gz.hs](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hs) | 104857600 | 7da22bd346ac4bf38f0855222a93b50f |
| [SEAMAPD21.tar.gz.ht](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ht) | 104857600 | 519fb0c6981ee74e221bd7ee8b7d6749 |
| [SEAMAPD21.tar.gz.hu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hu) | 104857600 | d5b34cb227037423387f4350850c633f |
| [SEAMAPD21.tar.gz.hv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hv) | 104857600 | 849ca2ef0061eebff3fff833531fc799 |
| [SEAMAPD21.tar.gz.hw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hw) | 104857600 | 3bf3fea4dbcad13957981a675d0e6cdd |
| [SEAMAPD21.tar.gz.hx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hx) | 104857600 | a6ae7a838a2498ee111d44b4f54661cb |
| [SEAMAPD21.tar.gz.hy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hy) | 104857600 | 460a1126f484c7ae8d3501f420eb19bf |
| [SEAMAPD21.tar.gz.hz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.hz) | 104857600 | 9e6db690a81fa8b86aeb502fe3b111cf |
| [SEAMAPD21.tar.gz.ia](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ia) | 104857600 | 27a56b0642fcacaee34b6a41b4fdfe85 |
| [SEAMAPD21.tar.gz.ib](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ib) | 104857600 | be7681426c0a66ca882fe660ac94efe4 |
| [SEAMAPD21.tar.gz.ic](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ic) | 104857600 | 6fde49c4fdde01d2955c5570295df26c |
| [SEAMAPD21.tar.gz.id](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.id) | 104857600 | 11ae40c1b4d2431592e270fdb687af9d |
| [SEAMAPD21.tar.gz.ie](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ie) | 104857600 | a3e138f4005fe451a3d16c4f232b6d1b |
| [SEAMAPD21.tar.gz.if](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.if) | 104857600 | e8af5aa74d6b103be4929b38f32c0422 |
| [SEAMAPD21.tar.gz.ig](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ig) | 104857600 | be583e7c960030872c081f24df9315c7 |
| [SEAMAPD21.tar.gz.ih](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ih) | 104857600 | 8e31c8399a2f427a5c544aab64d09ed8 |
| [SEAMAPD21.tar.gz.ii](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ii) | 104857600 | ebc17f2b4aa308b147f59ab6e561bf03 |
| [SEAMAPD21.tar.gz.ij](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ij) | 104857600 | 5626c8bff7493946f47fdfaee4886e9a |
| [SEAMAPD21.tar.gz.ik](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ik) | 104857600 | e85def8c5b19c56521d84ffb195015bb |
| [SEAMAPD21.tar.gz.il](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.il) | 104857600 | b7b0f07dc06849c1faf5476da7a75304 |
| [SEAMAPD21.tar.gz.im](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.im) | 104857600 | 7946c0fdf20ae87c62f0814d5199e696 |
| [SEAMAPD21.tar.gz.in](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.in) | 104857600 | db1ab132849c6e9e513ca6954f0b4237 |
| [SEAMAPD21.tar.gz.io](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.io) | 104857600 | 2dd42f90396e6f81b6e519527d927ad7 |
| [SEAMAPD21.tar.gz.ip](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ip) | 104857600 | 820022dd42829a4ded7079fe6f5e2de0 |
| [SEAMAPD21.tar.gz.iq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iq) | 104857600 | 59cd175d881270c72eaca7fecd2d0b46 |
| [SEAMAPD21.tar.gz.ir](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ir) | 104857600 | 59951709593cd6a4fb2814242dca731d |
| [SEAMAPD21.tar.gz.is](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.is) | 104857600 | baf19c8c8449f9c3837436e119011a21 |
| [SEAMAPD21.tar.gz.it](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.it) | 104857600 | 6a91146c0c2fa0bf34141cf5795c269a |
| [SEAMAPD21.tar.gz.iu](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iu) | 104857600 | b2154bb39b6feb534261571b268d6039 |
| [SEAMAPD21.tar.gz.iv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iv) | 104857600 | 18b48e8cf81183f544b8b826f0f92072 |
| [SEAMAPD21.tar.gz.iw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iw) | 104857600 | ffa57ab083fe4f746831a4c9494546a8 |
| [SEAMAPD21.tar.gz.ix](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ix) | 104857600 | eb3d93480e07746ab137b305e9f06a39 |
| [SEAMAPD21.tar.gz.iy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iy) | 104857600 | fd50bef8d0c4e9cda277f6abfc01bff2 |
| [SEAMAPD21.tar.gz.iz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.iz) | 104857600 | 36fc87bcab97048fc098e53d3b42f547 |
| [SEAMAPD21.tar.gz.ja](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ja) | 104857600 | 13aa26361de87dade1402019740646e3 |
| [SEAMAPD21.tar.gz.jb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jb) | 104857600 | 61ea9c76ab13ded14cf17249ece0297c |
| [SEAMAPD21.tar.gz.jc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jc) | 104857600 | e9d48ec130d86692154aa248ce16a528 |
| [SEAMAPD21.tar.gz.jd](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jd) | 104857600 | 860f75304539685534cb483b9f17d0aa |
| [SEAMAPD21.tar.gz.je](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.je) | 104857600 | 2bbd9213976fa004adad97776f55dd5f |
| [SEAMAPD21.tar.gz.jf](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jf) | 104857600 | 2e16e348f88748c4e65c95465fb91dd2 |
| [SEAMAPD21.tar.gz.jg](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jg) | 104857600 | b7841c04cf31255cf327fe2d5e94f692 |
| [SEAMAPD21.tar.gz.jh](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jh) | 104857600 | 7829c9866e9e77886d24a84917a381e4 |
| [SEAMAPD21.tar.gz.ji](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ji) | 104857600 | 48514cc5da41e54112b6d1f954f996a2 |
| [SEAMAPD21.tar.gz.jj](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jj) | 104857600 | 4ac2b96efb217acd6d29d406cc0cb753 |
| [SEAMAPD21.tar.gz.jk](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jk) | 104857600 | b51449e9f98c62af89c014e88811e419 |
| [SEAMAPD21.tar.gz.jl](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jl) | 104857600 | 80383051c48052b7fbacc3dafce25f59 |
| [SEAMAPD21.tar.gz.jm](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jm) | 104857600 | 8065cfaec6c5814b5954343e15e4bfac |
| [SEAMAPD21.tar.gz.jn](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jn) | 104857600 | 0c1d1bcc2895ae358439f0d83eab2ff7 |
| [SEAMAPD21.tar.gz.jo](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jo) | 104857600 | 7fc78ddc8f53b69278fd226b46dd3a53 |
| [SEAMAPD21.tar.gz.jp](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jp) | 104857600 | dbeae8a7e13d20e13a1f7a0211549092 |
| [SEAMAPD21.tar.gz.jq](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jq) | 104857600 | bb16f994743f3d82ecd06bd996f97a87 |
| [SEAMAPD21.tar.gz.jr](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jr) | 104857600 | 5c01fbea46ce48e6b96b58ddadfc707e |
| [SEAMAPD21.tar.gz.js](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.js) | 104857600 | 678bfec89ccc6e8f9453720206b4af7b |
| [SEAMAPD21.tar.gz.jt](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jt) | 104857600 | b3d3091fbb1c969a0263a0da7f4803b8 |
| [SEAMAPD21.tar.gz.ju](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ju) | 104857600 | fe42932006530d9d9b977b8e2cbb2517 |
| [SEAMAPD21.tar.gz.jv](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jv) | 104857600 | 491b869f3290140071c72ff963c24654 |
| [SEAMAPD21.tar.gz.jw](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jw) | 104857600 | e070c94b46bf5b6e7c1ab2c9b295ae08 |
| [SEAMAPD21.tar.gz.jx](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jx) | 104857600 | fd417de6270cba95ef96a69112a9e7fd |
| [SEAMAPD21.tar.gz.jy](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jy) | 104857600 | 3fcc42de6a2965e8bfb41329aafbd313 |
| [SEAMAPD21.tar.gz.jz](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.jz) | 104857600 | ab3f98dfde493475a34547f14bb14ef7 |
| [SEAMAPD21.tar.gz.ka](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.ka) | 104857600 | cf842b003d1e58dc66850ac349da268e |
| [SEAMAPD21.tar.gz.kb](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.kb) | 104857600 | 9bd7f6871c83a5b2633a73422a565bba |
| [SEAMAPD21.tar.gz.kc](https://grunt.sefsc.noaa.gov/parr/SEAMAPD21.tar.gz.kc) |  67908260 | 194ba6bde7323a8ea7a531dcf176a45f |



This repository is a scientific product and is not official communication of the National Oceanic and Atmospheric Administration, or the United States Department of Commerce. All NOAA GitHub project code is provided on an ‘as is’ basis and the user assumes responsibility for its use. Any claims against the Department of Commerce or Department of Commerce bureaus stemming from the use of this GitHub project will be governed by all applicable Federal law. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by the Department of Commerce. The Department of Commerce seal and logo, or the seal and logo of a DOC bureau, shall not be used in any manner to imply endorsement of any commercial product or activity by DOC or the United States Government.
