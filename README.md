# hmc5883l
C header only library for the hmc5883l compass sensor on RaspberryPi

## Example
```c
#include "hmc5883l/hmc5883l.h"

int main(int argc, char **argv) {
  HMC5883L hmc5883l;
  
  // Initialize
  if( hmc5883l_init(&hmc5883l) != HMC5883L_OKAY ) {
      fprintf(stderr, "Error: %d\n", hmc5883l._error);
      exit(1);
  }
  
  // Read
  hmc5883l_read(&hmc5883l);

  // Print results
  printf("X, Y, Z:\t%f | %f | %f", 
                hmc5883l->_data.x, 
                hmc5883l->_data.y, 
                hmc5883l->_data.z);

  printf("Scaled:\t%f | %f | %f", 
                hmc5883l->_data.x_scaled, 
                hmc5883l->_data.y_scaled, 
                hmc5883l->_data.z_scaled);

  printf("Orientation:\tDeg: %f | Rad: %f",
                hmc5883l->_data.orientation_deg,
                hmc5883l->_data.orientation_rad);
  
  return 0;
}
```
