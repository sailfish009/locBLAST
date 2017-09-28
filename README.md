<div style="color: black; font-family: 'times new roman', serif; font-size: 12pt; text-align: justify;">[![locBLAST Input](http://drive.google.com/uc?export=view&id=0BzYndv9w528iUktzRVc1bWs4RjA)](http://drive.google.com/uc?export=view&id=0BzYndv9w528iUktzRVc1bWs4RjA)  

This is a simple tutorial which explains how to design your own web interface for NCBI BLAST+ to perform local and online database search using PHP in webserver. The PHP library _loc_<span style="color:blue">BLAST</span> executes the NCBI BLAST+ programs using `exec()` function through passing parameters from the HTML form fields. In _loc_<span style="color:blue">BLAST</span>, two list boxes were used to select program & database, and text area & file upload is used to input query sequence in the FASTA file format. A FASTA file validation function is included to validate the query sequence before executing the BLAST programs. The _loc_<span style="color:blue">BLAST</span> PHP library and test database files were freely available at [GitHub](https://github.com/AshokHub/locBLAST/).

### Requirements for _loc_BLAST Setup

In this tutorial, I have given a brief explanation about embedding the latest NCBI BLAST+ (the latest version of NCBI BLAST+ as on September 29, 2017 is **2.60**.) in any PHP enabled web server. The latest version of NCBI BLAST+ (standalone command-line BLAST programs) can be downloaded from the FTP server of NCBI ([ftp://ftp.ncbi.nih.gov/blast/executables/blast+/LATEST](ftp://ftp.ncbi.nih.gov/blast/executables/blast+/LATEST)). A simple PHP supporting web server is enough to run the local BLAST program through the web browser. Follow the steps given below to setup and run the _loc_<span style="color:blue">BLAST</span> program.

**1.** Download the compressed NCBI BLAST+ software (I have downloaded [ncbi-blast-2.6.0+-x64-win64.tar.gz](ftp://ftp.ncbi.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.6.0+-x64-win64.tar.gz) for Windows 64-bit OS) from the NCBI FTP server.

**2.** Create a folder named **locBLAST** in the web directory (usually named **htdocs**, **www**, or **wwwroot**).

**3.** Decompress [ncbi-blast-2.6.0+-x64-win64.tar.gz](ftp://ftp.ncbi.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.6.0+-x64-win64.tar.gz) file and copy all the files present in the **bin** folder to **locBLAST** directory.

**4.** Download **index.php** and **db** folder from [GitHub](https://github.com/AshokHub/locBLAST/) and copy to **locBLAST** directory.

**5.** Open the URL [http://localhost/locBLAST](http://localhost/locBLAST) in the web browser to run _loc_<span style="color:blue">BLAST</span> program.

[![locBLAST in Browser](http://drive.google.com/uc?export=view&id=0BzYndv9w528iTWlGckdxUzVGZ0k "locBLAST in Browser.")](http://drive.google.com/uc?export=view&id=0BzYndv9w528iTWlGckdxUzVGZ0k)

**6.** Click the hyperlink **DEMO** and **Search** button to test local database search. The default parameters will generate an HTML file formatted BLAST search report.

[![locBLAST Output](http://drive.google.com/uc?export=view&id=0BzYndv9w528icVNmYU5CVDZtWlE "locBLAST in Browser.")](http://drive.google.com/uc?export=view&id=0BzYndv9w528icVNmYU5CVDZtWlE)

The form fields in _loc_<span style="color:blue">BLAST</span> program can be extended with custom form fields to perform advanced search. Moreover, desired database files can be downloaded from the NCBI FTP directory ([ftp://ftp.ncbi.nih.gov](ftp://ftp.ncbi.nih.gov)) and copied to the **db** directory to perform offline database search.

### Custom Database Creation

We can also create custom database using **makeblastdb** program present in the **locBLAST** directory. To create a custom database, copy the FASTA file formatted multiple sequence file to the **db** directory. Then open the **db** directory and press **ALT** key + **Right** mouse click to open command-line window directing to the current directory. Enter the command “`makeblastdb.exe -in db/pdt.fas -out db/pdt -dbtype prot -title PDTDB`” to create a custom database named **PDTDB** (already included in the **db** folder.

The FASTA file formatted multiple sequence file (**pdt.fas**)is given below:

<pre style="font-size: small;">>pdt|pdtdbt00001|pdb|1OKE|A/B
MRCIGISNRDFVEGVSGGSWVDIVLEHGSCVTTMAKNKPTLDFELIKTEAKQPATLRKYC
IEAKLTNTTTESRCPTQGEPTLNEEQDKRFVCKHSMVDRGWGNGCGLFGKGGIVTCAMFT
CKKNMEGKIVQPENLEYTVVITPHSGEEHAVGNDTGKHGKEVKITPQSSITEAELTGYGT
VTMECSPRTGLDFNEMVLLQMKDKAWLVHRQWFLDLPLPWLPGADTQGSNWIQKETLVTF
KNPHAKKQDVVVLGSQEGAMHTALTGATEIQMSSGNLLFTGHLKCRLRMDKLQLKGMSYS
MCTGKFKVVKEIAETQHGTIVIRVQYEGDGSPCKIPFEIMDLEKRHVLGRLITVNPIVTE
KDSPVNIEAEPPFGDSYIIIGVEPGQLKLNWFKK
>pdt|pdtdbt00002|pdb|4O6B|A/B
AHHHHHHSSGVDLGTENLYFQSNADSGCVVSWKNKELKCGSGIFITDNVHTWTEQYKFQP
ESPSKLASAIQKAHEEGICGIRSVTRLENLMWKQITPELNHILSENEVKLTIMTGDIKGI
MQAGKRSLRPQPTELKYSWKTWGKAKMLSTESHNQTFLIDGPETAECPNTNRAWNSLEVE
DYGFGVFTTNIWLKLKEKQDVFCDSKLMSAAIKDNRAVHADMGYWIESALNDTWKIEKAS
FIEVKNCHWPKSHTLWSNGVLESEMIIPKNLAGPVSQHNYRPGYHTQITGPWHLGKLEMD
FDFCDGTTVVVTEDCGNRGPSLRTTTASGKLITEWCCRSCTLPPLRYRGEDGCWYGMEIR
PLKEKEENLVNSLVTA
>pdt|pdtdbt00003|pdb|2IOK|A/B
SKKNSLALSLTADQMVSALLDAEPPILYSEYDPTRPFSEASMMGLLTNLADRELVHMINW
AKRVPGFVDLTLHDQVHLLECAWLEILMIGLVWRSMEHPGKLLFAPNLLLDRNQGKCVEG
MVEIFDMLLATSSRFRMMNLQGEEFVCLKSIILLNSGVYTFLSSTLKSLEEKDHIHRVLD
KITDTLIHLMAKAGLTLQQQHQRLAQLLLILSHIRHMSNKGMEHLYSMKCKNVVPLYDLL
LEMLDAHRLHAPTS
>pdt|pdtdbt00004|pdb|2Q1Y|A/B
MTPPHNYLAVIKVVGIGGGGVNAVNRMIEQGLKGVEFIAINTDAQALLMSDADVKLDVGR
DSTRGLGAGADPEVGRKAAEDAKDEIEELLRGADMVFVTAGEGGGTGTGGAPVVASIARK
LGALTVGVVTRPFSFEGKRRSNQAENGIAALRESCDTLIVIPNDRLLQMGDAAVSLMDAF
RSADEVLLNGVQGITDLITTPGLINVDFADVKGIMSGAGTALMGIGSARGEGRSLKAAEI
AINSPLLEASMEGAQGVLMSIAGGSDLGLFEINEAASLVQDAAHPDANIIFGTVIDDSLG
DEVRVTVIAAGFDVSGPGRKPVMGETGGAHRIESAKAGKLTSTLFEPVDAVSVPLHTNGA
TLSIGGDDDDVDVPPFMRR
>pdt|pdtdbt00005|pdb|3GGE|A/B/C
SMKGIEKEVNVYKSEDSLGLTITDNGVGYAFIKRIKDGGVIDSVKTICVGDHIESINGEN
IVGWRHYDVAKKLKELKKEELFTMKLIEPKKSSEA
>pdt|pdtdbt00006|pdb|2F9Q|A/B/C/D
MAKKTSSKGKLPPGPLPLPGLGNLLHVDFQNTPYCFDQLRRRFGDVFSLQLAWTPVVVLN
GLAAVREALVTHGEDTADRPPVPITQILGFGPRSQGVFLARYGPAWREQRRFSVSTLRNL
GLGKKSLEQWVTEEAACLCAAFANHSGRPFRPNGLLDKAVSNVIASLTCGRRFEYDDPRF
LRLLDLAQEGLKEESGFLREVLNAVPVDRHIPALAGKVLRFQKAFLTQLDELLTEHRMTW
DPAQPPRDLTEAFLAEMEKAKGNPESSFNDENLRIVVADLFSAGMVTTSTTLAWGLLLMI
LHPDVQRRVQQEIDDVIGQVRRPEMGDQAHMPYTTAVIHEVQRFGDIVPLGMTHMTSRDI
EVQGFRIPKGTTLITNLSSVLKDEAVWEKPFRFHPEHFLDAQGHFVKPEAFLPFSAGRRA
CLGEPLARMELFLFFTSLLQHFSFSVPTGQPRPSHHGVFAFLVSPSPYELCAVPRHHHH
>pdt|pdtdbt00007|pdb|3EAH|A/B
PKFPRVKNWEVGSITYDTLSAQAQQDGPCTPRRCLGSLVFPRKLQGRPSPGPPAPEQLLS
QARDFINQYYSSIKRSGSQAHEQRLQEVEAEVAATGTYQLRESELVFGAKQAWRNAPRCV
GRIQWGKLQVFDARDCRSAQEMFTYICNHIKYATNRGNLRSAITVFPQRCPGRGDFRIWN
SQLVRYAGYRQQDGSVRGDPANVEITELCIQHGWTPGNGRFDVLPLLLQAPDEPPELFLL
PPELVLEVPLEHPTLEWFAALGLRWYALPAVSNMLLEIGGLEFPAAPFSGWYMSTEIGTR
NLCDPHRYNILEDVAVCMDLDTRTTSSLWKDKAAVEINVAVLHSYQLAKVTIVDHHAATA
SFMKHLENEQKARGGCPADWAWIVPPISGSLTPVFHQEMVNYFLSPAFRYQPDPWKGSAA
KGTGITR
>pdt|pdtdbt00008|pdb|4PQE|A
EGREDAELLVTVRGGRLRGIRLKTPGGPVSAFLGIPFAEPPMGPRRFLPPEPKQPWSGVV
DATTFQSVCYQYVDTLYPGFEGTEMWNPNRELSEDCLYLNVWTPYPRPTSPTPVLVWIYG
GGFYSGASSLDVYDGRFLVQAERTVLVSMNYRVGAFGFLALPGSREAPGNVGLLDQRLAL
QWVQENVAAFGGDPTSVTLFGESAGAASVGMHLLSPPSRGLFHRAVLQSGAPNGPWATVG
MGEARRRATQLAHLVGCPPGGTGGNDTELVACLRTRPAQVLVNHEWHVLPQESVFRFSFV
PVVDGDFLSDTPEALINAGDFHGLQVLVGVVKDEGSYFLVYGAPGFSKDNESLISRAEFL
AGVRVGVPQVSDLAAEAVVLHYTDWLHPEDPARLREALSDVVGDHNVVCPVAQLAGRLAA
QGARVYAYVFEHRASTLSWPLWMGVPHGYEIEFIFGIPLDPSRNYTAEEKIFAQRLMRYW
ANFARTGDPNEPRDPKAPQWPPYTAGAQQYVSLDLRPLEVRRGLRAQACAFWNRFLPKLL
SAT</pre>

</div>
