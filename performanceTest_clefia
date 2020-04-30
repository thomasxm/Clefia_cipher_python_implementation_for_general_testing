## For source code of clefia cipher in Python see clefia_2.py
from clefia_2 import setKey, encrypt, decrypt, ksTable
import os, sys, psutil, timeit
from time import time, process_time
import binascii, codecs

if __name__ == "__main__":

    def memory_usage():
        process = psutil.Process(os.getpid())
        memory = process.memory_info()[0] / float(2 ** 20)
        return memory

    mess = int(codecs.encode(os.urandom(8), 'hex'), 16) # 8 bytes message converted to int
    key = 0xffeeddccbbaa99887766554433221100

    def my_function_clefia(mess, key, keySize = "SIZE_128"):
        #key schedule
        setKey(key, keySize)
        #encryption
        ctext = encrypt(mess)
        #decryption
        ptext = decrypt(ctext)
        return 0

    memo_sum = 0
    for i in range(1000):
        my_function_clefia(mess, key)
        pid = os.getpid()
        py = psutil.Process(pid)
        memo_sum += py.memory_info()[0]/2.**30
    memo_sum = memo_sum/1000
    print("Memory usage measured over 1000 iteration = ", memo_sum,"GB")

    print("RAM usage :",memory_usage())
    print("CPU usage in percenage:",psutil.cpu_percent())
    start_time_1 = time()
    start_time = process_time()
    my_function_clefia(mess, key)
    print("Excution time--- %s seconds ---" % (time() - start_time_1))
    print("CPU time --- %s seconds ---" % (process_time() - start_time))
    print("CPU percentage:", psutil.cpu_percent())
    print("RAM usage MB:", memory_usage())

    clock_time_sum = 0
    cpu_time_sum = 0
    for i in range(1000):
        start_time_1 = time()
        start_time = process_time()
        my_function_clefia(mess, key)
        cpu_time_sum += (process_time() - start_time)
        clock_time_sum += (time() - start_time_1)
    cpu_time_sum = cpu_time_sum/1000
    clock_time_sum = clock_time_sum/1000
    print("Clock time measured over 1000 iteration = ", clock_time_sum)
    print("CPU time measured over 1000 iteration:", cpu_time_sum)

    counter = 0
    print("(key schedule+encryption+decryption) for increasing input size")
    print("from 2 bytes to 268 MB")
    if (1==1):
        list = [2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048,2048*2,
        2048*2**2,2048*2**3,2048*2**4,2048*2**5,2048*2**6,2048*2**7,
        2048*2**8,2048*2**9,2048*2**10,2048*2**11,2048*2**12,2048*2**13,
        2048*2**14, 2048*2**15, 2048*2**16]
        print("Cipher capacity test clefia (time):")
        for bit in list:
            counter += 1
            print("  ", counter)
            mess = int(codecs.encode(os.urandom(bit), 'hex'), 16)
            start_time = time()
            my_function_clefia(mess, key)
            print("--- %s seconds ---" % (time() - start_time))

    if (1==1):
        list = [2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048,2048*2,
        2048*2**2,2048*2**3,2048*2**4,2048*2**5,2048*2**6,2048*2**7,
        2048*2**8,2048*2**9,2048*2**10,2048*2**11,2048*2**12,2048*2**13,
        2048*2**14, 2048*2**15, 2048*2**16]
        print("Cipher capacity test mode clefia (memory):")
        for bit in list:
            mess = int(codecs.encode(os.urandom(bit), 'hex'), 16)
            my_function_clefia(mess, key)
            pid = os.getpid()
            py = psutil.Process(pid)
            memoryUse = py.memory_info()[0]/2.**30  # memory use in GB
            print('memory use GB:', memoryUse)

### To calculate the throughput, one uses inputSize / execution time
### To calculate the cycles per bytes, one uses cycles per second / bytes per seconds
### = CPU speed (GHz or MHz) / throughput.
print("from 2 bytes to 268 MB")
if (1==1):
    list_mess = [2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048,2048*2,
    2048*2**2,2048*2**3,2048*2**4,2048*2**5,2048*2**6,2048*2**7,
    2048*2**8,2048*2**9,2048*2**10,2048*2**11,2048*2**12,2048*2**13,
    2048*2**14, 2048*2**15, 2048*2**16, 2048*2**17]
    print("Cipher throughpu test clefia:")
    for bit in list_mess:
        print(" message size in byte", bit)
        mess = int(codecs.encode(os.urandom(bit), 'hex'), 16)
        start_time = time.time()
        my_function_clefia(mess, key)
        print("--- %s throughput bytes/second ---" %(np.divide(bit,
        (time.time() - start_time))))
