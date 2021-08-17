this.FileReader.onload = (ev: any) => {
      console.log(ev.target.result);
    };
    this.itemDocument.onAfterAddingFile = (fileItem: any) => {
      this.FileReader.readAsText(fileItem._file);
    };

