<template>
    <div class="main">
        <div class="left">
            <Left></Left>
        </div>

        <div class="right">
            <div class="top">
                <img src="img/title.png" />
            </div>
            <div class="bottom">
                <Right></Right>
            </div>
        </div>
    </div>
</template>
<style>
* {
    padding: 0;
    margin: 0;
}
.left {
    width: 100px;
    float: left;
    margin-right: 10px;
}
.right {
    width: 1000px;
    float: left;
    margin-left: 10px;
}
.main {
    width: 1200px;
    margin: 20px auto;
}

.top img {
    height: 200px;
    width: 1000px;
}
.left,
.right {
    background-color: #f5f5f5;
    height: 500px;
}
</style>
<script>
import Left from "../components/Left.vue";
import Right from "../components/Right.vue";

export default {
    components: {
        Left,
        Right
    }
};

// Promise的用法
function test(resolve, reject) {
    var timeOut = Math.random() * 2;
    console.log("set timeout to: " + timeOut + " seconds.");
    setTimeout(function() {
        if (timeOut < 1) {
            console.log("call resolve()...");
            resolve("200 OK");
        } else {
            console.log("call reject()...");
            reject("timeout in " + timeOut + " seconds.");
        }
    }, timeOut * 1000);
}

var p1 = new Promise(test);
var p2 = p1.then(function(result) {
    console.log("成功：" + result);
});
var p3 = p2.catch(function(reason) {
    console.log("失败：" + reason);
});
</script>