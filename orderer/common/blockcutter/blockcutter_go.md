#### blockcutter.go

Cut a block according to "configtx.yaml".

A block will be cutted  when :
the messages meet the "MaxMessageCount" 
or the batch size exceed the "PreferredMaxBytes"
or the message request to be isolated into its own batch.

func (r *receiver) Ordered(msg *cb.Envelope) ([][]*cb.Envelope, [][]filter.Committer, bool)

The  function above returns [][] rather than [], considering the case when a message request to be isolated into its own batch,
and therefore 2 batchs shall return, one for the messages before, and one for the isolated one.