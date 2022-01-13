# Given an array of integers of size N, your task is to find the maximum j - i such that Arr[j] > Arr[i] where 0 &lt; = i &lt; j &lt; = N-1.
Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();

		int arr[] = new int[n];
		for(int i=0; i<n; i++){
			arr[i] = sc.nextInt();
		}

		//pre processing
		int min[] = new int[n];
		min[0] = arr[0];
		for(int i=1; i<n; i++){
			min[i] = Math.min(arr[i],min[i-1]);
		}

		int max[] = new int[n];
		max[n-1] = arr[n-1];
		for(int i=n-2; i>=0; i--){
			max[i] = Math.max(arr[i],max[i+1]);
		}

		//main task

		int i=0, j=0, diff=-1;
		while(i<n && j<n){
			if(min[i] < max[j]){
				diff = Math.max(diff,j-i);
				j = j+1;
			}else{
				i = i+1;
			}
		}
		System.out.print(diff);

