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
