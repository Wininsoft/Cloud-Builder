# �������ݲ���
ͨ���������ݲ����� ���ǿ���ֱ������һ��sql�������ݽ�������ɾ�������£����룬�������Ȱ����ݶ�ȡ��������ڴ��ٽ��в����� �Ӷ����Դ���������������ܡ�

ע�⣺
����������Ϊ �������ڴ棬���Բ��ᴥ��ʵ��ķ�������ݲ�������¼��������ʱ/�󣬸���ʱ/��ɾ��ʱ/�󣬱���ʱ/�� Ҳ���ᴥ��ʵ�����Ե�ֵ�ı�ʱ�䣬 ���Ҳ�����������޸���־��

### ����ɾ��

�﷨��
query.BatchDelete();

ʾ����
- ����ɾ��ȥ�����־��Ϣ
ApplicationData.LogSet.Where(w=>w.CreateTime.Year==DateTime.Now.Year-1).BatchDelete();

### ��������

�﷨��
query.BatchUpdate(updateLambda);

ʾ����
- �������¿ͻ����ݷ�����Ϊ�յĿͻ�����������ݷ�����Ϊ7��󣬲�������״̬Ϊ���ݷ�
ApplicationData.CustomerSet.Where(w=>w.NextVisitDate==null).BatchUpdate(item=>{
	item.NextVisitDate=DateTime.Today.AddDays(7),
	item.Status="���ݷ�"
})
- ������ҵ��ԱΪ01�Ŀͻ���ת��ҵ��Ա02
var newSalesman=ApplicationData.EmployeeSet.Where(w=>w.No=="01");//�õ�ҵ��Ա02��ʵ�����
ApplicationData.CustomerSet.Wheere(w=>w.SalesMan.No=="01").BatchUpdate(item=>item.SalesMan==newSalesman);//��������

### ��������
query.BatchInsert(insertLambda);

ʾ����
- �������������־�����ƶ�����ʷ��־��
var logQuery=ApplicationData.LogSet.Where(w=>w.CreateTime.Date==DateTime.Date.AddDays(-1));
logQuery.BatchInsert(s=>new ApplicationData.HistoryLog(){
	CreateTime=s.CreateTime
	Content=s.Content
});//�������Ƶ�HistoryLog��
logQuery.BatchDelete();//����ɾ��


