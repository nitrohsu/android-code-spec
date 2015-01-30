# Android Code Specification

## File Name
* 1) Component

    * XxxActivity
    * XxxFragment
    * XxxService

* 2) Menu icon

    * ic_action_xxx           //菜单图标，如需要共用此命名优先

* 3)  Notification icon

    * ic_notification_xxx     //通知栏图标

* 4)  ImageView default src icon

    * ic_default_xxx          //ImageView默认图片

* 5)  Other drawable

    * selector_xxx
    * shape_xxx

* 6)  Layout

    * activity_xxx    //activity view定义
    * frag_xxx        //fragment view定义
    * adapter_xxx     //adapter view定义
    * dialog_xxx      //dialog view定义
    * view_xxx        //其他片段 view定义
* 7)  Libs
    * lib name+version+add time

## Member Parameter Name
    1)  Java类型变量命名m开头;
    2)  View引用类型命名m开头,View结尾;
    3)  外部引用本组件的数据Key以DATA_XXX开头
    4)  本组件返回的数据Key以RST_XXX结尾

## 变量空间遵循Java Controlling Access

    Modifier    Class   Package Subclass    World
    public      Y       Y       Y           Y
    protected   Y       Y       Y           N
    no modifier Y       Y       N           N
    private     Y       N       N           N

## XML
* 1)  string字符串尽可能放入string.xml,便于国际化
* 2)  color定义直接写在布局文件里，其他主色值由style定义

## Other
* 01) 变量命名要准确说明含义，禁止直接使用引用类型作为变量名
* 02) 及时清理垃圾代码
* 03) 代码模块化

* 04) 非通用Adapter放入主Class内部，减少参数引用
* 05) BaseAdapter中context由parent获取，无需引入外部参考
* 06) 尽可能减少View组合嵌套使用，比如LinearLayout中TextView＋ImageView

* 07) Activity无需实现Actionbar Navigator HomeAsUp
* 08) 含有较多的SetOnClickListener时，XML中直接添加点击调用方法
* 09) Fragment中通过onAttach定义Context，不要使用getActivity()

* 10) 注释采用左对齐后注释;
* 11) 非必要时设置private;
* 12) Collection类型外部初始化

eg.
    GoodsDetailActivity.java:

    public static final String DATA_GOODS_ID="goods_id";

    private String mGoodsSerial = null;         //商品编码
    private TextView mGoodsSerialView = null;   //
    private ArrayList<GoodsInfo> mGoodsList = new ArrayList<GoodsInfo>();   //商品列表

    private String mGoodsId;

    private TextView mGoodsIdView;

    public void onCreate(Bundle bundle){
        super.onCreate(bundle);

        mGoodsId = getIntent().getStringExtra(DATA_GOODS_ID);

        setContent(R.layout.activity_goods_detail);

        mGoodsIdView = (TextView)findViewById(R.id.goods_detail_id);

        //...

        mGoodsIdView.setTextColor(Color.parserColor("#787878"));
    }


