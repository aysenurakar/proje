#include <stdio.h>
#include <time.h>


struct WorkTime {
    int yil, ay, gun, saat, dakika, saniye;
};


union EpochTime {
    struct tm timeStruct;
    time_t epochValue;
};


time_t convertToEpoch(struct WorkTime wt) {
    union EpochTime et;

    et.timeStruct.tm_year = wt.yil - 1900; 
    et.timeStruct.tm_mon = wt.ay - 1;    
    et.timeStruct.tm_mday = wt.gun;
    et.timeStruct.tm_hour = wt.saat;
    et.timeStruct.tm_min = wt.dakika;
    et.timeStruct.tm_sec = wt.saniye;
    et.timeStruct.tm_isdst = -1; 

    return mktime(&et.timeStruct);
}

int main() {
    struct WorkTime startTime, endTime;
    time_t epochStart, epochEnd;
    double timeDiff;
    int saat1, dakika1, saniye1;

    
    printf("Giris saatini giriniz (YYYY MM DD HH MM SS): ");
    scanf("%d %d %d %d %d %d", &startTime.yil, &startTime.ay, &startTime.gun,
          &startTime.saat, &startTime.dakika, &startTime.saniye);

   
    printf("Cikis saatini giriniz (YYYY MM DD HH MM SS): ");
    scanf("%d %d %d %d %d %d", &endTime.yil, &endTime.ay, &endTime.gun,
          &endTime.saat, &endTime.dakika, &endTime.saniye);

   
    epochStart = convertToEpoch(startTime);
    epochEnd = convertToEpoch(endTime);

   
    printf("\nGiris zamaninin Epoch degeri: %ld\n", epochStart);
    printf("Cikis zamaninin Epoch degeri: %ld\n", epochEnd);

    
    timeDiff = difftime(epochEnd, epochStart);

    saat1 = (int)(timeDiff / 3600);
    dakika1 = (int)((timeDiff - (saat1 * 3600)) / 60);
    saniye1 = (int)(timeDiff - (saat1 * 3600) - (dakika1 * 60));

    printf("\nToplam calisma suresi: %d saat, %d dakika, %d saniye\n", saat1, dakika1, saniye1);

    return 0;
}
