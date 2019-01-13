# Angular-Forms-Tutorial
Source code related to the angular forms tutorial on Youtube and Udemy

Reactive form

1)import ReactiveFormsModule and add to the declaration array
import { ReactiveFormsModule } from '@angular/forms';

2)import FormGroup,FormControl 
import { FormGroup, FormControl} from '@angular/forms';

FormGroup is like container for entire form.
it is used to represent entire form

FormControl is for each and every field of form

it is kind of model for form

registrationForm: FormGroup;
   registrationForm = new FormGroup({
    userName: new FormControl('Vishwas'),//
     password: new FormControl(''),
   confirmPassword: new FormControl(''),
   });
   
  3) provide formGrop in form tag
  <form [formGroup]="registrationForm" (ngSubmit)="onSubmit()">
  
  4) provide formControlName for each and every field
  <input type="text" formControlName="userName" class="form-control">
  
  
  19)Nested forms https://www.youtube.com/watch?v=B0a3IIQckBw&index=19&list=PLC3y8-rFHvwhwL-XH04cHOpJnkgRKykFi
  
  for the complex form in order to make it simple we can nest for into each other.
  i.e in user form we can make separate  group for address group for fields like 
   address: new FormGroup({
  //     city: new FormControl(''),
  //     state: new FormControl(''),
//     postalCode: new FormControl('')


20)Seting form data from component or from service from backend
we can set form data for update functionlity 

we can use setvalue or patchvalue method on formgroup 
for setvalue method we have to set value to the each and every formcontrol
for patchValue method we can to set value for few fields in  formcontrol


loadAPIData() {
    // this.registrationForm.setValue({
    //   userName: 'Bruce',
    //   password: 'test',
    //   confirmPassword: 'test',
    //   address: {
    //     city: 'City',
    //     state: 'State',
    //     postalCode: '123456'
    //   }
    // });

    this.registrationForm.patchValue({
      userName: 'Bruce',
      password: 'test',
      confirmPassword: 'test'
    });
}

22)Validations in Angular 2 

there are inbulid validations provided by angular.
import Validators 
import { Validators } from '@angular/forms';

apply the validators validations to form-field to the second filed in the field-contol array.
first field is for default name.if single vadidation there will be no need of array at second field.

userName: ['', [Validators.required, Validators.minLength(3)]]

use getter to get a reference to field to use it in HTML

 get userName() {
    return this.registrationForm.get('userName');
}

<input type="text" [class.is-invalid]="userName.invalid && userName.touched" formControlName="userName" class="form-control">
      <!-- <small class="text-danger" [class.d-none]="userName.valid || userName.untouched">Username is required</small> -->
      <div *ngIf="userName.invalid && userName.touched">
        <small class="text-danger" *ngIf="userName.errors?.required">Username is required</small>
        <small class="text-danger" *ngIf="userName.errors?.minlength">Username must be at least 3 characters</small>
        
</div>
where ? is safe navigation operator






