# 项目测试场景

#### 值得考虑在内的几个可能场景：

##### 1、“口罩检测”模型能否正常工作，识别是否有误

##### 2、“语音识别”模型能否正常工作，识别是否有误

##### 3、受检测人员是否配合软件检测，如果不配合该作何处理



## 测试场景

1、人员已佩戴口罩，检测结果为“已佩戴”，通过门禁

![img](http://m.qpic.cn/psc?/V10qPHDm2OqGNV/ruAMsa53pVQWN7FLK88i5jIcgr6jHvq3mD0gdeKoun66a.JPA0b7KLFq7Ayt9eoXINsQ7lE5*633t0u4NBKC.wpno6h.1orrwTZKWb*9BNY!/b&bo=AgblAAAAAAADB8M!&rf=viewer_4)

2、人员未佩戴口罩，检测结果为“未佩戴”，软件提示此时人员佩戴好口罩，并说出了“重新检测”，语音识别成功，口罩检测模型重新检测，检测结果为“已佩戴”，通过门禁

![img](http://m.qpic.cn/psc?/V10qPHDm2OqGNV/45NBuzDIW489QBoVep5mcRgLvuW8SbTfcxTaHFPeh6gl27jWx.gGwGMIW2BHLXY9hojK3GIs7czg8A1nn.Z5Kmybft.b1DlshbYcFvYpThA!/b&bo=5wb5AAAAAAADFyo!&rf=viewer_4)

3、人员未佩戴口罩，检测结果为“未佩戴”，软件提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”此时人员佩戴好口罩，并说出了“重新检测”，语音识别成功，口罩检测模型重新检测：检测结果为“未佩戴”，再次提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”，此时为佩戴口罩不规范或口罩模型识别失误，再次提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”重复以上过程

![img](http://m.qpic.cn/psc?/V10qPHDm2OqGNV/45NBuzDIW489QBoVep5mcRgLvuW8SbTfcxTaHFPeh6icRGxUb6MaAPNVJY24bae.GC2bQXmXUJ36TxVhb6quPAEHDuW4GV76g7T*kWBaDIE!/b&bo=ZQfJAQAAAAADF5g!&rf=viewer_4)

4、人员未佩戴口罩，检测结果为“未佩戴”，软件提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”但人员并不说出“重新检测”，则需要在一定的时间间隔后重新提示，注意这个时间间隔要考虑人员拿出、佩戴口罩的时间，如果第二次提示后人员仍然不说出“重新检测”，超过时间间隔后，软件显示“***识别失败***”，进行下一个人员的检测

![img](http://m.qpic.cn/psc?/V10qPHDm2OqGNV/45NBuzDIW489QBoVep5mcRgLvuW8SbTfcxTaHFPeh6jgNeTZFvIaaos.VOpKHzb3xEmp7BdHnlgbscdmqFlZ5d*OOeyjof15N*yrx4au9zA!/b&bo=FweuAAAAAAADF4w!&rf=viewer_4)

5、人员未佩戴口罩，检测结果为“未佩戴”，软件提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”人员说出了“重新检测”，但语音模型识别失效（即未识别到“重新”、“检测”等字眼），软件再次提示“**请佩戴口罩，佩戴完成后，请说出‘重新检测’。**”如果提示超过3次，语音模型仍然识别失效，软件显示“***识别失败***”，进行下一个人员的检测

![img](http://m.qpic.cn/psc?/V10qPHDm2OqGNV/45NBuzDIW489QBoVep5mcZLgjxyaufypx68BWPgUX2DBAdeBqTMGc3fcr.P9tveUX.HgTyY*k8FQn.R2k4ng0qj3ONFfvqZ1xaMMktEQm*E!/b&bo=8QZkAwAAAAADF6I!&rf=viewer_4)

