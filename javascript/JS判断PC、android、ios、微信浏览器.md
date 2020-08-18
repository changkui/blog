通过js userAgent来判断
-----------------

判断访问此链接的操作系统

    var Agents = new Array("Android", "iPhone", "SymbianOS", "Windows Phone", "iPad", "iPod");
    var flag = true;
    
    /**
     * 初始化加载程序
     */
    window.onload = function(){
        console.log(isMobile());
        console.log(isWechat());
        console.log(getOsVersion());
    }
    
    /**
     * 判断是不是移动端
     * @returns {boolean}
     */
    function isMobile() {
        var userAgentInfo = navigator.userAgent;
        for (var v = 0; v < Agents.length; v++) {
            if (userAgentInfo.indexOf(Agents[v]) > 0) {
                flag = false;
                break;
            }
        }
        document.write("是否移动端-"+ !flag+"//");
        return "是否移动端-" + !flag;
    }
    
    /**
     * 判断是不是微信浏览器
     * @returns {boolean}
     */
    function isWechat() {
        var ua = navigator.userAgent.toLowerCase();
    
        if(ua.match(/MicroMessenger/i)=="micromessenger"){
            document.write("是微信浏览器//");
            return "是微信浏览器";
        }
        else{
            document.write("不是微信浏览器//");
            return "不是微信浏览器";
        }
    }
    
    /**
     * 判断浏览器所在机器操作系统版本
     */
    function getOsVersion(){
        var u = navigator.userAgent,version = '';
        if (u.indexOf('Mac OS X') > -1) {
            //ios
            var regStr_saf = /OS [\d._]*/gi;
            var verinfo = u.match(regStr_saf);
            version ="ios" + (verinfo + "").replace(/[^0-9|_.]/ig,'').replace(/_/ig,'.');
            document.write("ios");
        } else if (u.indexOf('Android') > -1
            || u.indexOf('Linux') > -1) {
            //android
            version ="android" + u.substr(u.indexOf('Android') + 8, u.indexOf(";", u.indexOf("Android")) - u.indexOf('Android') - 8);
            document.write("android");
        } else if (u.indexOf('BB10') > -1) {
            //黑莓bb10系统
            version ="黑莓bb10系统" +  u.substr(u.indexOf('BB10') + 5, u.indexOf(";", u.indexOf("BB10")) - u.indexOf('BB10') - 5);
            document.write("黑莓bb10系统");
        } else if (u.indexOf('IEMobile')) {
            //windows phone
            version ="windows phone";
            document.write("windows phone")
        }
        return version;
    }

