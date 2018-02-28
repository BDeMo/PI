
package pi;

import java.util.ArrayList;
import java.util.List;

import org.json.JSONArray;

public class result{
    public String item;
    public String type;
    public	String[] basic_words;
    public int byte_offset;
    public int byte_length;
    public result(String item, String type,	JSONArray basic_words, int byte_offset, int byte_length){
    	List<String> bw_list = new ArrayList<String>();
    	this.item = item;
    	this.type = type;
    	for(int i = 0; i < basic_words.length(); i++){
    		bw_list.add(basic_words.getString(i));
    	}
    	this.basic_words = (String[])bw_list.toArray(new String[bw_list.size()]);
    	this.byte_offset = byte_offset;
    	this.byte_length = byte_length;
    }
}