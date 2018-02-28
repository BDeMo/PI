package pi;

import java.io.FileOutputStream;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

import org.apache.poi.hssf.usermodel.HSSFCell;
import org.apache.poi.hssf.usermodel.HSSFRow;
import org.apache.poi.hssf.usermodel.HSSFSheet;
import org.apache.poi.hssf.usermodel.HSSFWorkbook;


public class Typesetting {
	private static List<bufferNode> outBuffer;
	public void TypeSet(result[] arg0){
		outBuffer = new ArrayList<bufferNode>();
		bufferNode tempNode = new bufferNode();
		bufferNode tempNode1 = new bufferNode();
		
		List<result> TargetList = new ArrayList<result>();
		tempNode.setTitle("名称");
		tempNode.setList(new ArrayList<String>());
		for (result result : arg0) {
			if(result.type.equals("n")){
				TargetList.add(result);
				tempNode.getList().add(result.item);
			}
		}
		outBuffer.add(tempNode);
		tempNode = new bufferNode();
		tempNode.setTitle("数量");
		tempNode1.setTitle("单位");
		tempNode.setList(new ArrayList<String>());
		tempNode1.setList(new ArrayList<String>());
		for (int i = 0; i < TargetList.size(); i++) {
			result tempResult = null;
			for (int j = 0; j < arg0.length; j++){
				if(arg0[j].type.equals("m")
						&&	arg0[j].byte_offset < TargetList.get(i).byte_offset){
					tempResult = arg0[j];
				}
			}
			tempNode.getList().add(tempResult.basic_words[0]);
			tempNode1.getList().add(tempResult.basic_words[1]);
		}
		outBuffer.add(tempNode);
		outBuffer.add(tempNode1);
	}
	public void outputFromBuffer(String position)
			throws IOException{
		HSSFWorkbook wkb = new HSSFWorkbook();
		HSSFSheet sheet = wkb.createSheet("sheet0");
		HSSFRow row = sheet.createRow(0);
		for (int i = 0; i < outBuffer.size(); i++){
			row.createCell(i).setCellValue(outBuffer.get(i).getTitle());
		}
		for (int i = 0; i < outBuffer.get(0).getList().size(); i++){
			row = sheet.createRow(i+1);
			for (int j = 0; j < outBuffer.size(); j++){
				row.createCell(j).setCellValue(outBuffer.get(j).getList().get(i));
			}
		}
		FileOutputStream output = new FileOutputStream(position);
		wkb.write(output);
		output.flush();
	}
}
