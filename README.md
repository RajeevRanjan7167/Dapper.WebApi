columnDefs = [
    { headerName: 'FileName', field: 'FileName' },
    { headerName: 'FileSize', field: 'FileSize' },
    { headerName: 'FileType', field: 'FileType' }
  ];


  onFileChange(evt: any) {
    debugger;
    //this.templateData = undefined;    
    this.templateData = new MatTableDataSource();
    this.templateColumn = [];
    this.tempFinalData = [];
    const target: DataTransfer = <DataTransfer>(evt.target);

    if (target.files.length == 0) {
      this.clearFileField();
      return;
    }

    if (target.files.length > 1) {
      Swal.fire('', 'Cannot use multiple files', 'error');
      this.clearFileField();
      return;
    }

    for (let i = 0; i < this.itemDocument.queue.length; i++) {
      let fileItem = this.itemDocument.queue[i]._file;
      // if (fileItem.type != 'application/vnd.ms-excel' && fileItem.type != 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet') {
      //   Swal.fire('', "Please select only excel file.", 'error');
      //   this.clearFileField();
      //   return;
      // }
      // if (fileItem.size > 5242880) {
      //   Swal.fire('', "File should be less than 5 MB of size.", 'error');
      //   this.clearFileField();
      //   return;
      // }

      debugger;
      const reader: FileReader = new FileReader();
      reader.readAsBinaryString(target.files[0]);
      reader.onload = (e: any) => {
        const bstr: string = e.target.result;
        const wb: XLSX.WorkBook = XLSX.read(bstr, { type: 'binary' });
        const wsname: string = wb.SheetNames[0];
        const ws: XLSX.WorkSheet = wb.Sheets[wsname];
        this.exceldata = XLSX.utils.sheet_to_json(ws, { range: "A1:D1", header: 1 });

        

        this.UpdateDataTbl.push({ "FileName": fileItem.name, "FileSize": fileItem.size, "FileType": fileItem.type })
        this.rowData = this.UpdateDataTbl;       
      }
      console.log(this.exceldata,'Test');
    }
