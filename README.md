public rowData = []
  public UpdateDataTbl = [];
  public tempFinalData;
  public NoDataFound = false;
  public templateColumnData = [];
  public itemDocument: FileUploader = new FileUploader({ isHTML5: true, disableMultipart: false });

  templateColumn: string[] = [];
  templateData = new MatTableDataSource();
  PostingData = [];


  FileReader: FileReader = new FileReader();


  @ViewChild('sheetForm') sheetForm: NgForm;
  exceldata: AOA = [];
  wopts: XLSX.WritingOptions = { bookType: 'xlsx', type: 'array' };
  public importMode;
  public tempexcelData;
  public isyearMonth;
  public isAmountType;
  public isDocumentStatus;
  public YearsList;
  public moduleId;
  public templateId;
  selection = new SelectionModel(true, []);
  public advanceFilterobserbable;
  public advanceFilterValues = null;
  public amountStatusMaster;

  constructor() { }

