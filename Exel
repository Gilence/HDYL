import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.FileInputStream;
import java.io.IOException;

import javax.swing.JButton;
import javax.swing.JFileChooser;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.filechooser.FileNameExtensionFilter;

import org.apache.poi.hssf.usermodel.HSSFCell;
import org.apache.poi.hssf.usermodel.HSSFRow;
import org.apache.poi.hssf.usermodel.HSSFSheet;
import org.apache.poi.hssf.usermodel.HSSFWorkbook;

public class Exel extends test_Frame{
	public static void main(String args[]) throws IOException{
		 test_Frame tf = new test_Frame();
		 
		FileInputStream fis=new FileInputStream(location);
		HSSFWorkbook workbook=new HSSFWorkbook(fis);	
		int rowindex=0;
		int columnindex=0;
		//시트 수 (첫번째에만 존재하므로 0을 준다)
		//만약 각 시트를 읽기위해서는 FOR문을 한번더 돌려준다
		HSSFSheet sheet=workbook.getSheetAt(0);
		//행의 수
		int rows=sheet.getPhysicalNumberOfRows();
		for(rowindex=1;rowindex<rows;rowindex++){
		    //행을 읽는다
		    HSSFRow row=sheet.getRow(rowindex);
		    if(row !=null){
		        //셀의 수
		        int cells=row.getPhysicalNumberOfCells();
		        for(columnindex=0;columnindex<=cells;columnindex++){
		            //셀값을 읽는다
		            HSSFCell cell=row.getCell(columnindex);
		            String value="";
		            //셀이 빈값일경우를 위한 널체크
		            if(cell==null){
		                continue;
		            }else{
		                //타입별로 내용 읽기
		                switch (cell.getCellType()){
		                case HSSFCell.CELL_TYPE_STRING:
		                    value=cell.getStringCellValue()+"";
		                   String clean = value.replaceAll("[^0-9]", "");
		                    break;
		                default :
		                	break;
		            }
		            System.out.println("각 셀 내용 :"+value);
		            }
		        }
		}
	}
}
	

public class test_Frame extends JFrame implements ActionListener{
	public static  String location;
	 private JFileChooser jfc = new JFileChooser();
     private JButton jbt_open = new JButton("열기");
     private JButton jbt_save = new JButton("저장");
     private JLabel jlb = new JLabel(" ");
     public test_Frame(){
             super("test");
             this.init();
             this.start();
             this.setSize(400,200);
             this.setVisible(true);
     }
     public void init(){
             getContentPane().setLayout(new FlowLayout());
             add(jbt_open);
             add(jbt_save);
             add(jlb);
     }
     public void start(){
             jbt_open.addActionListener(this);
             jbt_save.addActionListener(this);

             jfc.setFileFilter(new FileNameExtensionFilter("txt", "txt"));
             // 파일 필터
             jfc.setMultiSelectionEnabled(false);//다중 선택 불가
     }

     @Override
     public void actionPerformed(ActionEvent arg0) {
             // TODO Auto-generated method stub
             if(arg0.getSource() == jbt_open){
                     if(jfc.showOpenDialog(this) == JFileChooser.APPROVE_OPTION){
                             location = jfc.getSelectedFile().toString();
                             String tempFileName = jfc.getSelectedFile().getName();
                             jlb.setText("이름 : " + tempFileName +" 시 간 ");
                             
                     }
             }
     }
}}
             
             
     



