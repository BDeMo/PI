package pi;


import java.util.ArrayList;
import java.util.List;

import org.json.JSONArray;
import org.json.JSONObject;

import com.baidu.aip.nlp.AipNlp;

public class CloudApi {
	
	public static final String APP_ID = "9384640";
	public static final String API_KEY = "IgY9esawypm4e8KFq947pHo6";
	public static final String SECRET_KEY = "LFeHVCpDGC5k7tnIZNzXsimL0uLbLSmS";
	public static result[] Operate(String arg0){
		
        AipNlp client = new AipNlp(APP_ID, API_KEY, SECRET_KEY);
        
        String text = arg0;
        JSONObject ori_result = client.lexer(text);
        //https://cloud.baidu.com/doc/NLP/NLP-FAQ.html#NLP-FAQ
        JSONArray items = ori_result.getJSONArray("items");
        int length = items.length();
        System.out.println(ori_result.toString());
        List<result> ansl = new ArrayList<result>();
        for(int i=0;i<length;i++){
            JSONObject obj = items.getJSONObject(i);
            
            String type = new String(obj.getString("pos"));
            String item = new String(obj.getString("item"));
            JSONArray basic_words = obj.getJSONArray("basic_words");
            int byte_length = obj.getInt("byte_length");
            int byte_offset = obj.getInt("byte_offset");
            ansl.add(new result(item, type, basic_words, byte_offset, byte_length));
        }
        return (result[])ansl.toArray(new result[ansl.size()]);
	}
	
}
