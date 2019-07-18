编辑模态HTML代码

```html
<modal tit="{{ i.id > 0 ? '编辑 【' + i.name + '】 ' : '创建新' }}$1">
  <form nz-form #f="ngForm" (ngSubmit)="save()">
    <div se-container col="1">
      $0
    </div>
    <ng-template #footer>
      <button nz-button type="button" (click)="close()">关闭</button>
      <button nz-button nzType="primary" [disabled]="f.invalid" [nzLoading]="http.loading">
        保存
      </button>
    </ng-template>
  </form>
</modal>
```