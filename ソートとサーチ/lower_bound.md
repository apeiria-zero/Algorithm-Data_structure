# lower_bound

Created: Apr 15, 2020 3:38 PM
Property: ape iria
Property 2: No
Tags: Algorithm

left は常に条件を満たさない

right は常に条件を満たす

right - left = 1 になるまで範囲を狭める (最後は right が条件を満たす最小)

    #include <stdio.h>
    #include <stdbool.h>
    #define N 10
    
    static int a[]={2,3,7,11,31,50,55,70,77,80};
    
    bool isOK(int mid,int key){
        if(a[mid]>=key)return true;
        else return false;
    }
    
    int binary_search(int key){
        int left = -1;
        int right = N+1;
    
        while(right - left>1){
            int mid = left + (right - left)/2;
            if(isOK(mid,key)) right=mid;
            else left = mid;
        }
        return right;
    }
    
    void main(void) {
        int key;
        int ans=0;
        printf("search data >"); scanf("%d",&key);
        ans=binary_search(key);
        printf("%d ",ans);
    }