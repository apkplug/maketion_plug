# maketion_plugAPI文档

验证功能

public void authenticateAccount(String pkey,String psign,String name);

public boolean checkAuthentication();

public void clearAuthentication();
验证功能包括三个函数：authenticateAccount()提交验证；checkAuthentication()判断验证状态；clearAuthenticationh()清除验证状态。 参数key：由脉可寻名片识别服务申请获得；

设置Sdcard图片缓存路径

public void setSavePath(String path)；
设置Sdcard路径后，拍摄名片所生成的图片，会保持在此路径下。

使用相机拍照并获取名片信息

public void takepic(PlugMkxBackUpload callback);
获取名片信息

public void getCardsWithTime(long time,PlugMkxBackCards callback);

public void getCardsWithUUID(String[] uuids,PlugMkxBackCards callback);
获取名片信息有两种方式：通过名片的关键字uuid获取名片信息；获取一个时间点之后的所有名片信息。

参数uuids：字符串数组，每个字符串为一个名片的uuid；

参数time：时间点， 1970年1月1日开始经过的“秒”（数若此参数为0表示获取所有名片信息，不包含已删除的名片和无法识别的名片）；

类

PlugMkxCard

成员变量
    类型   名称

    String address;

    int  audit;

    String carduuid;

    String cname;

    long creatime;

    String duty;

    String email;

    String fax;

    String fields;

    int flag;

    String logo;

    String mobile1;

    String mobile2;

    String name;

    String tell1;

    String tell2;

    long updatetime;

    String website;
回调接口

    public interface PlugMkxBackCards {
        public void onBack(int code, String info, ArrayList<PlugMkxCard> cards);
        //参数code：网络调用状态；
        //参数errInfo：当网络调用失败时，返回错误参考信息；
        //参数cards：返回的名片信息数组。

    }

    public interface PlugMkxBackUpload {
        public void onBack(int code, String errInfo, String uuid, int status);
        //参数code：网络调用状态；
        //参数errInfo：当网络调用失败时，返回错误参考信息；
        //参数uuid：当前上传名片uuid；
        //参数status：STATUS_START表示开始上传，STATUS_SUCESS表示上传成功，STATUS_ERROR表示上传失败。

    }
