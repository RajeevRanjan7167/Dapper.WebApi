onFileChange(ev) {


    debugger;
    let workBook = null;
    let jsonData = null;
    const reader = new FileReader();
    const file = ev.target.files;

    debugger;

    for (let i = 0; i < file.length; i++) {
      this.UpdateDataTbl.push({ "FileName": file[i].name, "FileSize": file[i].size, "FileType": file[i].type })
      this.rowData = this.UpdateDataTbl;
    }

    reader.onload = (event) => {
      const data = reader.result;
      workBook = XLSX.read(data, { type: 'binary' });
      jsonData = workBook.SheetNames.reduce((initial, name) => {
        const sheet = workBook.Sheets[name];
        initial[name] = XLSX.utils.sheet_to_json(sheet);
        return initial;
      }, {});
      const dataString = JSON.stringify(jsonData);
      document.getElementById('output').innerHTML = dataString.slice(0, 300).concat("...");
      debugger;
      this.setDownload(dataString);
    }
    reader.readAsBinaryString(file);
  }


  setDownload(data) {
    this.willDownload = true;
    setTimeout(() => {
      const el = document.querySelector("#download");
      el.setAttribute("href", `data:text/json;charset=utf-8,${encodeURIComponent(data)}`);
      el.setAttribute("download", 'xlsxtojson.json');
    }, 1000)
  }
