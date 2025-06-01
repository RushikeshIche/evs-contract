// SPDX-License-Identifier: MIT
pragma solidity ^0.8.30;
import "hardhat/console.sol";
contract EVS {
    //OWNER SETUP - START
    address private owner;
    event OwnerSet(address indexed oldOwner, address indexed newOwner);
    modifier isOwner() {
        require(msg.sender == owner, "Caller is not owner");
        _;
    }
    constructor() {
        owner = msg.sender;//Here Contract Deployer 
        emit OwnerSet(address(0), owner);
    }
    function changeOwner(address newOwner) public isOwner {
        require(newOwner != address(0), "New owner should not be the zero address");
        emit OwnerSet(owner, newOwner);
        owner = newOwner;
    }
    function getOwner() external view returns (address) {
        return owner;
    }
    //OWNER SETUP - END

    event CandidateAdded(address candidate);
    event CandidateRemoved(address candidate);
    event VoteCast(address voter, address candidate);



    mapping (address=>address)private votes;
    mapping (address=>uint256) candidates;
    mapping (address=>bool) isCandidate;
    address[] candidatesArr;
    mapping (address=>uint256) votersVoted;

    function addCandidate(address add) public isOwner{
        for(uint256 i = 0 ; i < candidatesArr.length; i++){
            if(add==candidatesArr[i]){
                return;
            }
        }
        candidatesArr.push(add);
        candidates[add]=0;
        isCandidate[add]=true;
    }
    function removeCandidate(address add) public isOwner{
        for (uint256 i = 0; i < candidatesArr.length; i++) {
        if (candidatesArr[i] == add) {
            candidatesArr[i] = candidatesArr[candidatesArr.length - 1];
            candidatesArr.pop();
            break;
        }
    }
    delete candidates[add];
    }
    function giveVote(address toCandidate)public{
        require(isCandidate[toCandidate], "Invalid candidate");

        if(votersVoted[msg.sender]==0)
        {
                votes[msg.sender]=toCandidate;
                votersVoted[msg.sender] = 1;
                candidates[toCandidate]++;
        }
    }
    function getAllCandidates() public view returns (address[] memory) {
        return candidatesArr;
    }
    function getWinner()public view returns(address) {
        //here no case considered of multiple winners with same vote
        address winner;
        uint256 maxi = 0;
        for(uint256 i = 0 ; i < candidatesArr.length ; i++){
            if(candidates[candidatesArr[i]]>maxi){
                maxi = candidates[candidatesArr[i]];
                winner = candidatesArr[i];
            }
        }
        return winner;
    }
    function getVotes(address add)public view returns(uint256) {
        return candidates[add];
    }
    function resetElection()public isOwner{
        for (uint i = 0; i < candidatesArr.length; i++) {
            delete candidates[candidatesArr[i]];
        }
        delete candidatesArr;
    }
}
