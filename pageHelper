/**
 * @name 前端分页辅助函数
 * @author Simless
 * @createTime 2016-08-24 17:10:30
 * @description 
 */


var pageHelper = {
	/**
	 * 
	 * @param {Object} json
	 * @param {String} pageNum
	 * @param {String} pageSize
	 */
	start : function(json, pageNum, pageSize){
		if(json && json.length && pageNum>0 && pageSize>0){
			
			var total = json.length; //总记录数
			var totalPage = Math.ceil(total/pageSize);//总页数
			var hasLastPage = pageNum <= 1 ? false : true;//是否有上一页
			var hasNextPage = pageNum >= totalPage ? false : true;//是否存在下一页
			var start = (pageNum-1)*pageSize;
			var end = pageNum*pageSize-1;
			var list = {};
			if(pageNum < totalPage){			
				for(var i=start;i<=end; i++){
					list[i] = json[i];
				}
			}else if(pageNum == totalPage){
				for(var i=start;i<=total-1; i++){
					list[i] = json[i];
				}
			}else{
				list = null;
			}
			return {
				"start" : start,
				"end" : end,
				"pageNum" : pageNum,
				"pageSize" : pageSize,
				"total" : total,
				"totalPage" : totalPage,
				"hasLastPage" : hasLastPage,
				"hasNextPage" : hasNextPage,
				"list" : list
			}
		}else{
			return {
				"message" : "传入参数有误"
			}
		}
	}
};

$(document).ready(function(){
	$.getJSON('./page.json',function(data){
		if(data.result == 1){
			var json = data.data;
			var obj = pageHelper.start(json, 2, 8);
			console.log(obj.list);
		}
	});
});
