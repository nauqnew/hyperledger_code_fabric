
// checkpointInfo
type checkpointInfo struct {
	latestFileChunkSuffixNum int   //第几个区块文件
	latestFileChunksize      int   //这个文件的大小
	isChainEmpty             bool
	lastBlockNumber          uint64
}

//checkpointInfo以“blkMgrInfo”为key存储在db中。


func newBlockfileMgr(id string, conf *Conf, indexConfig *blkstorage.IndexConfig, indexStore *leveldbhelper.DBHandle) *blockfileMgr {

1. 获取ledger存储的路径, 如果没有则创建 : blockStorageDir/chains/chainId , 如blockStorage/chains/prodchannel1
2. 从db获取checkpointInfo, 如果为空，初始化为{0，0，true，0}，并写入db
3. 比较checkpointInfo与文件系统存储是否一致，如果不一致，同步checkpointInfo. (func syncCPInfoFromFS)
4. 创建currentFileWriter，把未完整保存的区块信息剔除掉。checkpointInfo中保存是的最近一个完整的区块。
5. 创建区块索引。mgr.syncIndex() 有点复杂，还没细看。
6. 初始化并更新BlockchainInfo.

}



// fileLocPointer
type fileLocPointer struct {
	fileSuffixNum int
	locPointer struct {
		offset      int
		bytesLength int
	}
}



func (mgr *blockfileMgr) addBlock(block *common.Block) error {


}