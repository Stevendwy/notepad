##js判断键盘大写锁定
 	var capsLockKey = e.keyCode ? e.keyCode : e.which;
	var shifKey = e.shiftKey ? e.shiftKey:((capsLockKey == 16) ? true : false);
	if(((capsLockKey >= 65 && capsLockKey <= 90) && !shifKey)||((capsLockKey >= 97 && capsLockKey <= 122) && shifKey)){
	    return true;
	}else{
	    return false;
	}