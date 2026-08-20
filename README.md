<!-- 一鍵複製按鈕 -->
<button id="copyBtn" onclick="copyText()">📋 一鍵複製</button>

<style>
#copyBtn{
  border:none;
  border-radius:14px;
  padding:11px 20px;
  font-size:14.5px;
  font-weight:600;
  background:#8B6F4E;
  color:#fff;
  cursor:pointer;
}
#copyBtn:active{ background:#6E5638; }
</style>

<script>
function copyText(){
  // 這裡放你想要複製的內容
  const textToCopy = "這裡放要複製的文字";

  if(navigator.clipboard && navigator.clipboard.writeText){
    navigator.clipboard.writeText(textToCopy).then(
      ()=> alert('已複製！'),
      ()=> fallbackCopy(textToCopy)
    );
  } else {
    fallbackCopy(textToCopy);
  }
}

function fallbackCopy(text){
  try{
    const ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.focus();
    ta.select();
    
