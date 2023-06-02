pragma solidity >=0.7.0 <0.9.0;

contract Voting {
    address penyelenggara;

    struct Calon {
        string nama;
        uint jumlahVote;
    }

    mapping(address => bool) private pemilih;
    
    Calon[] private namaCalon;

    constructor (string[] memory namaKandidat) {
        for (uint i=0; i < namaKandidat.length; i++) {
           namaCalon.push(Calon(namaKandidat[i], 0)); 
        }
        // namaCalon.push(Calon(namaKandidat, 0));
    }

    function tampilkanKandidat(uint indexKandidat) public view returns(string memory, uint) {
        require(indexKandidat < namaCalon.length, "Salah Nomor");
        Calon memory kandidat = namaCalon[indexKandidat];
        return(kandidat.nama, kandidat.jumlahVote);
    }

    function hitungKandidat() public view returns(uint) {
        return namaCalon.length;
    }

    function vote(uint indexKandidat) public {
        require(indexKandidat < namaCalon.length, "Salah Nomor");
        require(!pemilih[msg.sender], "Anda sudah memilih");
        namaCalon[indexKandidat].jumlahVote++;
        pemilih[msg.sender] = true;
    }

    function tambahKandidat(string memory inputKandidat) public {
        namaCalon.push(Calon(inputKandidat, 0)); 
    }
}
