# ��ѯ

ͨ����ѯ��䣬ƽ̨��Ѳ�ѯ��䷭���sql��䷢�͸� �ײ�����Դ����ִ�У�Ȼ�󷵻�ǿ���͵Ĳ�ѯ�����

### ��ѯ�������ȫ������

�﷨��
[����Դ].[��]Set������[����Դ]Ϊ����Դ�����ƣ�[��]Ϊ������ơ�
ʾ����
- ApplicationData.CustomerSet
��ʾ��ѯApplicationData����ԴCustomer���ȫ������
���ɵ�sql���ο���
select * from [Customer]

### ����

�﷨��
��ѯ.Where(lambda)�� ���� lambda��ʾҪ�Բ�ѯ���й��˵Ĳ�������lambda���ʽ

ʾ����
- ApplicationData.CustomerSet.Where(w=>w.Type=="Personal")
��ѯType�ֶε�ֵ����Personnal�Ŀͻ�
���ɵ�sql���ο���
select * from [Customer] as [it] where [it].[Type]=='Personal'

- ApplicationData.CustomerSet.Where(w=.w.Type=="Personal"&&w.NextVisitDate==DateTime.Today)
��ѯType�ֶ�ֵ����Personal������NextVisitDateֵ���ڽ�̩��Ŀͻ�
���ɵ�sql���ο���
select * from [Customer] as [it] where [it].[Type]=='Personal' and w [it]NextVisitDate==convert(getdate() as date)

### ����

�﷨��
��ѯ.OrderBy(lambdad)������
��ѯ.OrderByDescending(lambdad)������
��ѯ.ThenBy(lambdad)����������
��ѯ.ThenByDescending(lambdad)�����ӽ���

��������/�������򣬽���/���ӽ���������ǣ� �����ѯ�Ѿ������� ������/����Ḳ�ǵ���ѯ��ԭ�е����򣬶���������/���򲻻ᣬ������ԭ�в�ѯ��������Ͻ�һ������

ʾ����
- ApplicationData.CustomerSet.OrderBy(o=>o.CreateTime)
���մ���ʱ��Կͻ���������
���ɵ�sql���ο���
select * from [Customer] as [it] order by [it].[CreateTime]

- ApplicationData.CustomerSet.OrderByDescending(o=>o.CreateTime)
���մ���ʱ��Կͻ����н���
���ɵ�sql���ο���
select * from [Customer] as [it] order by [it].[CreateTime] desc

- ApplicationData.SalesOrderSet.OrderBy(o=>o.Customer).ThenByDescending(o=>o.Amount)
�����۶����Ȱ��տͻ�����Ȼ���ս����н���
���ɵ�sql���ο���
select * from [Customer] as [it] order by [it].[Customer], [it].[Amount] desc

### ��ҳ

�﷨��
��ѯ.Take(int pageSize); ��ȡ��������������
��ѯ.Skip(int startIndex); �Ӹ����кſ�ʼ��ȡ����

ʾ����
- ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Take(20)
��ȡ���۶����������20������

ʾ����
- ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Skip(20)
��ȡ���۶������ս����ĵ�20����ʼ������

- ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Skip(100).Take(20)
��ȡ���۶���������ĵ�100��120����
