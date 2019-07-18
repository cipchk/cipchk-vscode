构建一个 `Modal` 组件

```ts
import { Component, OnInit, ChangeDetectorRef, ChangeDetectionStrategy } from '@angular/core';
import { _HttpClient } from '@delon/theme';
import { NzModalRef } from 'ng-zorro-antd';
import { MessageService } from '@core';

const URI = `$1`;

@Component({
  selector: '$2',
  templateUrl: './$3.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class $4Component implements OnInit {
  i: { [key: string]: any };
  loading = false;

  constructor(
    private http: _HttpClient,
    private msg: MessageService,
    private modal: NzModalRef,
    private cdr: ChangeDetectorRef
  ) {}

  private setLoading(status = true): this {
    this.loading = status;
    this.cdr.detectChanges();
    return this;
  }

  ngOnInit(): void {
    this.setLoading()
      .http
      .get(URI + this.i.id)
      .subscribe(res => {
        this.i = res;
        this.setLoading(false);
      });
  }

  save() {
    this.setLoading()
        .http
        .post(``, this.i)
        .subscribe(() => {
          this.msg.suc();
          this.modal.close(true);
        }, () => this.setLoading(false));
  }

  close() {
    this.modal.destroy();
  }
}

```