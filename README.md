<div fxFlex="100" fxFlex.gt-sm="33.33" fxFlex.sm="50" class="p-2">
    <div class="upload" >
        <button color="primary" mat-raised-button class="uploadButton" multiple>Browse</button>
        <input type="file" (change)="onFileChange($event)" name="upload" id="fileControl" ng2FileSelect [uploader]="itemDocument" accept=".xlsx,.xls" />
        <span class="fileName">
            <span *ngIf="itemDocument?.queue?.length == 0">Select file..</span>
        </span>
    </div>
</div>

