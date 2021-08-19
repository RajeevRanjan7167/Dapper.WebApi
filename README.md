https://stackblitz.com/edit/angular-7-registration-login-example?file=app%2F_guards%2Fauth.guard.ts


var obj = {
  "  employee   name": "Sumit Vishwakarma",
  "employee id ": 001,
  "email ": "abc@gmail.com",
  "mobile  no": 9999999999,
};

Object.keys(obj).forEach((key) => {
   var replacedKey = key.trim().toUpperCase().replace(/\s\s+/g, "_");
   if (key !== replacedKey) {
      obj[replacedKey] = obj[key];
      delete obj[key];
   }
});
console.log(obj);





var processedJson = yourJson.replace(/( +)(?=[(\w* *]*":)/g, "_");
var yourObj = JSON.parse(processedJson);


// Iterate over array
arr.forEach(function(e, i) {
  // Iterate over the keys of object
  Object.keys(e).forEach(function(key) {
    
    // Copy the value
    var val = e[key],
      newKey = key.replace(/\s+/g, '_');
    
    // Remove key-value from object
    delete arr[i][key];

    // Add value with new key
    arr[i][newKey] = val;
  });
});

console.log(arr);


function replaceSpaces(data) {
    debugger;
    for (var i = 0; i < data.length; i++) {
        var obj = data[i];
        for (var key in obj) {
            var replacedKey = key.split(' ').join('_');
            data[i][obj] = replacedKey;
        }
    }

    return data;
}
