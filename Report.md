Kernel is the center of Operating system which handles memory management. 

In FreenNOS-1.0.3/lib/libarch/MemoryContext.h, there are functions defined for managing the virtual memory and mapping an address VM to physical memory.
    
    Line 106: 
    
        for mapping a virtual address to physical address in RAM 
        
		    virtual Result map(Address virt, Address phys, Memory::Access access) = 0;
            
    Line 128: 
    
        Translates virtual addres to physical address 
        
		    virtual Result lookup(Address virt, Address *phys) const = 0;

In FreenNOS-1.0.3/lib/libarch/MemoryContext.c, 

	Line 106 for the function release():
    
        //first translates the given virtual address to physical address then checks if that physical address exists then it releases it (deallocates it)
		    
            MemoryContext::Result MemoryContext::release(Address virt) 

    FreeNOS uses principle of paging for partitioning its logical address space and physical memory. 
    
	    Line 147:maps physical pages to virtual addresses 
        
	    	virtual Result mapRangeContiguous(Memory::Range *range)
		
In FreeNOS-1.0.3/lib/libarch/MemoryMap.h, 

	Line 52: 
		//this defines the memory regions on the system which are for virtual memory ranges 
		typedef enum Region
		    {
			KernelData,    /**<< Kernel program data from libexec, e.g. code, bss, (ro)data */
			KernelPrivate, /**<< Kernel dynamic memory mappings */
			UserData,      /**<< User program data from libexec, e.g. code, bss, (ro)data */
			UserHeap,      /**<< User heap */
			UserStack,     /**<< User stack */
			UserPrivate,   /**<< User private dynamic memory mappings */
			UserShare,     /**<< User shared dynamic memory mappings */
			UserArgs       /**<< Used for copying program arguments and file descriptors */
		    }
		    
		
