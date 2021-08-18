
<div fxFlex="100" fxFlex.gt-sm="33.33" fxFlex.sm="50" class="p-2">
    <div class="upload">
        <button color="primary" mat-raised-button class="uploadButton" >Browse</button>
        <input type="file" name="upload" id="fileControl" (change)="onFileChange($event)" accept=".xlsx,.xls" multiple/>

        <span class="fileName">
            <span *ngIf="itemDocument?.queue?.length == 0">Select file..</span>
        </span>
    </div>
</div>
