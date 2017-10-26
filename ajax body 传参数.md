##ajax body 传参数

	post
	let _url = `${hostPort}/link_007account`
	        let _obj = {
	                username:username
	            }
	        $.ajax({
	            url: _url,
	            type: 'POST',
	            dataType: 'json',
	            data: JSON.stringify(_obj),
	            success:function(res){
	                alert(res)
	            }
	        })