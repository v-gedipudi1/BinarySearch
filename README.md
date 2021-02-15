import java.io.*;
import java.util.*;

public class bsearch {
	public static void main(String [] args) {
		String[] arr = setinput();
		sort(arr);
		String target = args[0];
		int index = search(arr,target);
		if (index == -1) {
			System.out.println(target + " not found ");
		} 
		else {
			System.out.println(target + " found at " + index);
		} 
	} 
	public static String[] setinput() {
		final int length = 1000;
		String arr[] = new String[length];
		Scanner input = new Scanner(System.in);
		int i = 0;
		while(i<length && input.hasNextLine()) {
			arr[i] = input.nextLine();
			i++;
		} 
		String[] output = new String[i];
		int j = 0;
		while(j<i){
			output[j] = arr[j];
			j++;
		} 
		return output;
	} 
	public static String[] sort(String[] input) {
		int i = 0;
		int j = 1;
		while(i < input.length-1) {
			String tempString;
			int smallestElement = i;
			j = 1 + i;
			while(j<=input.length - 1) {
				if(input[smallestElement].compareTo(input[j]) > 0) {
					smallestElement=j;
				} 
				j++;
			} 
			tempString=input[smallestElement];
			input[smallestElement] = input[i];
			input[i] = tempString;
			i++;
		    }
		return input;
	}
	public static int search(String [] s, String target) {
		int begin = 0;
		int end = s.length - 1;
		while(begin <= end) {
			int middle = (begin + end) /2; 
			if(target.compareTo(s[middle]) > 0) {
				begin = middle + 1;
			} 
			else if (target.compareTo(s[middle]) < 0) {
				end = middle -1;
			} 
			else if (target.compareTo(s[middle]) == 0) {
				return middle;
			} 
		} 
		return -1;
	} 
} 
