# STM32 Based Token Number Display System

### AIM:
To develop a single sided PCB board for a single digit token number display system with buzzer.

### Requirement:
* proteus software
* CUBE IDE software
### Procedure:
#### STEP 1: 
Open proteus software and draw the schematic diagram.
#### STEP 2: 
Open pcb layout and convert it to 3d view.
#### STEP 3: 
Open IDE software configure the I/O pins.
#### STEP 4: 
Write the code for seven segment display and buzzer.
#### STEP 5: 
Uplode the elf file and run.

### Schematic:



### Code:
```
~~~
void display(int n)
{
		int x[11][8]={{0,0,1,1,1,1,1,1},{0,0,0,0,0,1,1,0},{0,1,0,1,1,0,1,1},{1,1,0,0,1,1,1,1},{0,1,1,0,0,1,1,0},{0,1,1,0,1,1,0,1},{0,1,1,1,1,1,0,1},{0,0,0,0,0,1,1,1},{0,1,1,1,1,1,1,1},{0,1,1,0,0,1,1,1}};
		if(n>=0 && n<10)
		{
			if(x[n][0]==1)
				HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
			else
				HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);

			if(x[n][1]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_SET);
			else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);

			if(x[n][2]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
			if(x[n][3]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_RESET);
			if(x[n][4]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_RESET);
			if(x[n][5]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
			if(x[n][6]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_RESET);
			if(x[n][7]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_RESET);

		}
		else
		{
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_RESET);

		}

}
/* USER CODE END 0 */

/**
  * @brief  The application entry point.
  * @retval int
  */
int main(void)
{
  /* USER CODE BEGIN 1 */
	GPIO_PinState s1;
	int count=0;
  /* USER CODE END 1 */

  /* MCU Configuration--------------------------------------------------------*/

  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();

  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* Configure the system clock */
  SystemClock_Config();

  /* USER CODE BEGIN SysInit */

  /* USER CODE END SysInit */

  /* Initialize all configured peripherals */
  MX_GPIO_Init();
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */
	  display(count);
	  s1=HAL_GPIO_ReadPin(GPIOB, GPIO_PIN_0);
	  if(s1==GPIO_PIN_RESET)
	  {
		  count = (count+1)%10;
		  HAL_Delay(500);

	  }
	  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_1, GPIO_PIN_SET);
	  		  HAL_Delay(3000);
	  		  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_1, GPIO_PIN_RESET);
    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
}
~~~
```
### PCB Layout:

![Screenshot 2023-04-24 110838](https://user-images.githubusercontent.com/65499285/233920276-3ef2a3cc-cda2-4e40-8255-ebb8c105eef3.png)

#### TopLayer:

![Screenshot 2023-04-24 110824](https://user-images.githubusercontent.com/65499285/233920231-ee96c0ea-20cb-4e57-90e3-9312bd1cdae3.png)

#### BottomLayer:
![image](https://user-images.githubusercontent.com/65499285/235099368-1df410ce-d866-4d57-a4da-d4afe1463bb5.png)

### 3D View:
![image](https://user-images.githubusercontent.com/65499285/235099324-ffc8dd62-0957-4f60-9a1b-3a9a9e795e19.png)

### Result:
Thus the simulation of token number display with buzzer is executed succesfully.
