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

