```
<input type="text" id="search" placeholder="Search...">
<button type="submit" id="search-button">Search</button>

<script>
function search() {
  var searchTerm = document.getElementById("search").value;
  var xhr = new XMLHttpRequest();
  xhr.open("GET", "/search?q=" + searchTerm);
  xhr.onload = function() {
    if (xhr.status === 200) {
      var results = JSON.parse(xhr.responseText);
      var ul = document.createElement("ul");
      for (var i = 0; i < results.length; i++) {
        var li = document.createElement("li");
        li.innerHTML = results[i].title;
        ul.appendChild(li);
      }
      document.getElementById("search-results").appendChild(ul);
    } else {
      console.log("Error searching: " + xhr.status);
    }
  };
  xhr.send();
}
</script>


```

